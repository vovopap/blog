---
layout: post
title: "CouchDB: challenges of building an offline-first mobile application"
description: "How to create offline-first application using CouchDB/PouchDB. In this article, I will address many questions regarding CouchDB db structure, data access layer for CouchDB/PouchDB, and several other gotchas"
tags: ["CouchDB", "PouchDB", "Ionic", "Offline app", "mobile app"]
---
Contents:
1. [Introduction](#intro)
1. [Database structure: a paradigm shift](#db-structure)
1. [Authentication & Authorization](#auth)
1. [Offline & Challenges of synchronization](#offline)
1. [Conclusion](#conclusion)

{:#intro}
## 1. Introduction
As the title says, this article is going to be all about challenges I have encountered building an offline-first mobile application with CouchDB and my solutions to them. My solutions/approaches are in no way perfect or the only way. That's why I wrote this article - I want you to share your suggestions in the comments section. 

I decided to write this post as a story. A story of 3-4 months of sitting on my couch. By the way, do you remember CouchDB saying to you "Relax"?

![Joey and Chandler on the couch](/assets/joey_chandler_on_couchdb.jpeg)

Personally, I don't really remember relaxing. Anyway, CouchDB does its job!

So, let's do it.
{:#db-structure}
## 2. Database structure: a paradigm shift
Before starting the project, I already had a well-defined database schema in SQL and at first, it was kind of awkward trying to squeeze an SQL schema into NoSQL. For example, am I going to have 30 CouchDB databases if I have 30 tables?

Not really, as it turns out. It made sense to apply the following steps for each type of relationship in my SQL schema:

**One-to-one.** They both go into one CouchDB db. For example, if you have `seller-account` relationship, you would have a db named `seller` and have `account` data as its property:

`seller` table:

id | name     | address                
---|----------|------------------------
123|Ali Carter|Sevens Street, 7, 100077

`account` table:

id | seller_id | card              | expiry  
---|-----------|-------------------|--------
342|123        |8888 8888 8888 8888|10/17   

The above two tables get merged into one db:
```javascript
{
  "id": "123",
  "name": "Ali Carter",
  "address": "Sevens Street, 7, 100077",
  "account": { // <- nested here
    "card": "8888 8888 8888 8888",
    "expiry": "10/17"
  }
}
```

**One-to-many.** This relationship is not much different from one-to-one, except instead of an object you have an array as a property. Let's change the previous example and assume one seller has many accounts. Then, we would achieve the following:

```javascript
{
  "id": "123",
  "name": "Ali Carter",
  "address": "Sevens Street, 7, 100077",
  "accounts": [{ // <- nested here
    "card": "8888 8888 8888 8888",
    "expiry": "10/17"
  }, {
    "card": "7777 7777 7777 7777",
    "expiry": "10/18"
  }]
}
```

**Many-to-many.** In this scenario, we have three tables forming the relation and they get mapped into two dbs. As an example, let's take Stackoverflow's badges. In Stackoverflow, one user can have many badges and one badge could belong to many users. So, we have the following many-to-many structure:

`user` table:

username | name      | reputation 
---------|-----------|------------
user123  |Ali Carter |78120       
user456  |Joey Jey   |45454       

`badge` table:

id | title  
---|--------
1  | Gold   
2  | Silver 
3  | Bronze 

`user_badge` table

id | username | badge_id | assigned_at     
---|----------|----------|------------
1  |user123   |1         |2019/10/10
2  |user123   |2         |2019/10/12
3  |user456   |4         |2019/10/13
4  |user456   |2         |2019/10/14

The above three tables get translated into the following two dbs:

`user` db:

```javascript
{
  "username": "user123",
  "name": "Ali Carter",
  "reputation": 78120,
  "badges": [
    1,
    2
  ]
}
```

`badge` db:


```javascript
{
  "id": "1",
  "title": "Gold"
  // you could have users array here, but that depends on your application logic
}
```
The next came the concerns of data integrity. With SQL data integrity is achieved naturally through table schemas: there is a well-defined set of constraints on what you can insert. On the other hand, a CouchDB database is by default loose and absolutely anything can be inserted as a document. 

CouchDB validates data using design documents. More specifically, using validation guards. And, interestingly these documents are stored among other documents in your db. Such a design approach is very clever. To understand why it is clever, we first need to understand CouchDB's replication feature (a killer feature).

CouchDB is designed with scaling in mind. You can have several CouchDB instances spread across many servers constantly in sync with each other. If you decide to add one more CouchDB instance, all you have to do is to create the dbs in this new instance and activate replications. All the existing data will flow in and since design documents are treated the same way as other documents they also get replicated automatically.

In short, a validation guard is a function which either completes (meaning document is valid) or throws an error, in which case insertion fails. Let's create a validation guard for one of the examples above. An example document from `user` db:

```javascript
{
  "_id": "myidhere123sgdgmsmkncnsmsms",
  "_rev": "1-73bdn73udnxnnnx787779nxnx",
  "username": "user123",
  "name": "Ali Carter",
  "reputation": 78120,
  "badges": [
    1,
    2
  ]
}
```
our validation document:

```
{
  "_id": "_design/_validation_guard",
  "language": "javascript",
  "validate_doc_update": "..."
}
```
`validate_doc_update` function:
```javascript
function(newDoc, oldDoc, userCtx, secObj) {
    function require(field, message) {
        message = message || "Document must have a " + field;
        if (!newDoc[field]) throw({forbidden : message});
    };
    
    function validateNumber(field, message) {
        message = message || "doc." + field + " must be number";
        if(typeof newDoc[field] !== "number") throw({forbidden : message});
    };
    
    function validateArray(field, message) {
        message = message || "doc." + field + " must be array";
        if(!Array.isArray(newDoc[field])) throw({forbidden : message});
    };
    
    require('username');
    require('name');
    validateNumber('reputation');
    require('badges');
    
    if (oldDoc) { // validate all updates
        if (oldDoc.username !== newDoc.username) {
            throw({forbidden: 'doc.username can not be changed.'});
        }
    }
}
```

Now, CouchDB calls our validation function every time a document is created or updated. The function checks if a) `username` and `name` are set, b) `reputation` is a number, c) `badges` is an array. Additionally, it also makes sure that `username` is never changed once the document is created.

One last thing in this section. I have realized that it is a bad idea to think SQL-way when reasoning about NoSQL db. Forget the SQL concepts (tables, columns, foreign keys) and its best practices. Read CouchDB's [documentation](https://docs.couchdb.org/en/stable/index.html) and start new.

{:#auth}
## 3. Authentication & Authorization

CouchDB has very good support for user authentication & authorization. It has a special db named `_user` and special endpoints for signup, signin, logout, change password, etc. What troubled me, though, was document-level access control.

Unfortunately, CouchDB as of writing this article has no support for document-level access control. The reason for such design decision is performance/scaling capabilities, which otherwise would be compromized. But, I believe there is some work/discussions happening on this issue and soon they will roll out this much needed feature. Read more [here](https://github.com/pouchdb/express-pouchdb/issues/262), [here](https://stackoverflow.com/questions/30295304/per-document-user-access-control-for-pouchdb-couchdb), and [here](https://news.ycombinator.com/item?id=14950060).

A common solution to this is to create a db per user and allow only that user to access the db. But, I believed it would be nightmare to maintain so many databases. For my application logic, it was fine if users could read others data as long as writes are not allowed.

I used Ionic Framework v3 as a basis for my app and PouchDB to store user data locally. Remember I was trying to build an offline-first application. CouchDB coupled with its loyal brother, PouchDB, simply gives you that capability. Read more about PouchDB [here](https://pouchdb.com)

I used PouchDB Authentication plugin to handle authentication & authorization. This plugin is a nice wrapper around CouchDB's outh endpoints. The following code snippet shows how to log in using PouchDB Authentication plugin:

```typescript
import PouchDB from 'pouchdb';
import PouchDBAuthentication from 'pouchdb-authentication';

// letting PouchDB know about our plugin
PouchDB.plugin(PouchDBAuthentication);

let remoteDb = new PouchDB('url/to/couchdb/instance/db_name');
remoteDb.logIn('username', 'password');
// ta-dah! We are logged in

```
Controlling write access was straightforward and was achieved using validation guards. The following validation function allows create/update/delete actions only within the scope of currently logged-in user. That is, a user can create/update/delete only his own records. But, let's not forget the admin who is king.

```javascript
function(newDoc, oldDoc, userCtx, secObj) {
    
    if (newDoc._deleted === true) {
        // only owner or admin can delete records
        if (userCtx.roles.indexOf('_admin') !== -1) {
            return;
        } else if(userCtx.name == oldDoc.owner) {
            return;
        } else {
            throw({forbidden: 'only owner or admin can delete records'});
        }
    }
    
    if (oldDoc) { // validate update
        if (oldDoc.owner !== userCtx.name && userCtx.roles.indexOf('_admin') === -1) {
            throw({forbidden: 'only owner or admin can update records'});
        }
    } else {
        if (newDoc.owner !== userCtx.name && userCtx.roles.indexOf('_admin') === -1) {
            throw({forbidden: 'only owner or admin can create records'});
        }
    }
}
```

{:#offline}
## 4. Offline & Challenges of synchronization

It was easy to setup data syncronization between remote CouchDB and local PouchDB. The replication can run once and terminate when everything until that moment is synced. Or it can sync data continuously waiting for future changes and terminate only when cancelled by the client.

One-time replication:
```typescript
// pull data from remoteDb
localDb.replicate.from(remoteDb)
    .on('complete', function (res) {
        console.log("replication complete", res);
    })
    .on('error', function (err) {
        console.log("handle error", err)
    });

// push data to remoteDb
localDb.replicate.to(remoteDb)
    .on('complete', function (res) {
        console.log("replication complete", res);
    })
    .on('error', function (err) {
        console.log("handle error", err)
    });

// this does both ways at once
PouchDB.sync(localDb, remoteDb)
    .on('complete', function (res) {
        console.log("replication complete", res);
    })
    .on('error', function (err) {
        console.log("handle error", err)
    });
```
Continuous replication:
```typescript
localDb.replicate.from(remoteDb, {
    live: true,
    retry: true,
    continuous: true
})
.on('paused', function (err) {
    console.log("replication paused (e.g. replication up to date, user went offline)", err);
})
.on('active', function () {
    console.log("replicate resumed (e.g. new changes replicating, user went back online)")
})
.on('denied', function (err) {
    console.log("a document failed to replicate (e.g. due to permissions)", err)
})
.on('error', function (err) {
    console.log("handle error", err)
});
```

Oh yeah! I can hear CouchDB saying "Relax, man. I will take care of it".

Not so fast. When the number of active live replications reached a certain number (5-6), some replications would silently fail. After some googling, I found that my application reached the [maximum parallel requests](https://github.com/pouchdb/pouchdb/issues/5012). The first 5-6 dbs get connected to remote db while others wait forever in line.

Goodbye, live sync.

I had two ways to solve this problem:
1. Write a service that synces each db serially using one-time replication. setTimeout(), baby!
2. Create a nodejs server that listens to global_changes feed and emits events when any change happens in any db. Each client would then listen to these events and run one-time replications only when needed.

The advantage of #1 is easy implementation. The disadvantage is a lot of unnecessary requests to the remote CouchDB, especially if no changes are being made.

The advantage of #2 is that one-time replication is issued only when needed. The disadvantages are nuanced implementation and a new point of failure.

I chose the former and here is my code:

```typescript
import { YourProvider } from 'your.provider';
import { MyProvider } from 'my.provider';
import { HisProvider } from 'his.provider';
import { HerProvider } from 'her.provider';
import { OurProvider } from 'our.provider';

export class ReplicationManager {
    private queuedProviders;
    private syncing: boolean = false;

    constructor(
        private yourProvider: YourProvider,
        private myProvider: MyProvider,
        private hisProvider: HisProvider,
        private herProvider: HerProvider,
        private ourProvider: OurProvider) {

        this.queuedProviders = [
            this.yourProvider,
            this.myProvider,
            this.hisProvider,
            this.herProvider,
            this.ourProvider
        ];
    }

    public syncAllDBs() {
        // first runs one-time replication per db, then kicks off the periodic synchronization
        return Promise.all(this.couchProviders.map(provider => provider.syncOnce())).then(() => {
            this.activateSyncQueue();
        });
    }

    private activateSyncQueue() {
        this.syncing = true;
        this.next(this.queuedProviders[0]);
    }

    private next(provider) {
        setTimeout(() => {
            if(this.syncing === false) return;

            // each provider has syncOnce function that does one-time replication
            provider.syncOnce()
            .on('complete', (res) => {
                let nextIndex = this.queuedProviders.indexOf(provider) + 1;
                if(nextIndex >= this.queuedProviders.length) nextIndex = 0;
                // once complete, calls itself for the next provider in queue
                this.next(this.queuedProviders[nextIndex]);
            })
            .on('error', err => {
                let nextIndex = this.queuedProviders.indexOf(provider) + 1;
                if(nextIndex >= this.queuedProviders.length) nextIndex = 0;
                // calls itself even when error occurs, could be some network issue - we want to survive network changes
                this.next(this.queuedProviders[nextIndex]);
            });
        }, 1000 * 60 * 1); // waits a minute
    }
}

```
Each provider above corresponds to a db. `syncAllDBs()` is called once at the time of application bootstrap. The function synces all dbs up until that moment and future changes are synced periodically using `setTimeout` of 1 minute.

Actually, there is one more solution (which I found out later). [socket-pouch](https://github.com/pouchdb-community/socket-pouch) is an adapter that proxies all PouchDB APIs to a remote CouchDB using WebSockets. It runs on a Node.js server.

Now, let's talk about data access layer. I found it both sensical and practical to create a data provider per db. Each provider implements an interface which I call `BaseInterface`:

``` typescript
export interface BaseInterface {
    setup(username, password): Promise<any>;

    getDbName();

    oneTimeSync();

    liveSync();

    reset();
}
```

Here is a provider which `implements` this interface:

```typescript
import { BaseInterface } from './base.interface';
import PouchDB from 'pouchdb';

export class ProductProvider implements BaseInterface {

    private localDb: any;
    private remoteDb: any;
        
    public setup(username, password): Promise<any> {
        let dbName = this.getDbName();
        this.localDb = new PouchDB(dbName);
        this.remoteDb = new PouchDB('/url/to/couchdb_instance/' + dbName);
        return this.remoteDb.logIn(username, password);
    }

    public getDbName() {
        return 'product';
    }

    public oneTimeSync() {
        let dbName = this.getDbName();
        return this.localDb.replicate.from(this.remoteDb)
          .on('complete', function (res) {
            console.log("[" + dbName + "] replication complete", res);
          }).on('error', function (err) {
            console.log("[" + dbName + "] handle error", err)
          });
    }

    public liveSync() {
        let dbName = this.getDbName();
        return this.localDb.replicate.from(this.remoteDb, {
            live: true,
            retry: true,
            continuous: true
        }).on('paused', function (err) {
            console.log("[" + dbName + "] replication paused (e.g. replication up to date, user went offline)", err);
          }).on('active', function () {
            console.log("[" + dbName + "] replicate resumed (e.g. new changes replicating, user went back online)")
          }).on('denied', function (err) {
            console.log("[" + dbName + "] a document failed to replicate (e.g. due to permissions)", err)
          }).on('error', function (err) {
            console.log("[" + dbName + "] handle error", err)
          });
    }

    public reset() {
        let logout$ = this.remoteDb.logOut();
        let destroy$ = this.localDb.destroy().then(() => {
            let dbName = this.getDbName();
            this.localDb = new PouchDB(dbName);
        });
        return Promise.all([logout$, destroy$]);
    }

    // db-specific data access functions
    public getAll() {
        return this.localDb.allDocs()
    }

    public create(data) {
      return this.localDb.post(data);
    }

    public update(data) {
      return this.localDb.push(data);
    }

    public delete(data) {
      data._deleted = true;
      return this.localDb.push(data);
    }
}
```

`BaseInterface` has five abstract functions, which every child provider will implement. 
`setup()` is where all the initialization should happen: create local PouchDB and login to the remote db. `getDbName()`, `oneTimeSync()`, and `liveSync()` do what their names suggest they do. It is important to call `reset()` when logging user out of the system. This clears local db and disconnects from remote db. We also have db-specific data access functions like list, create, update, delete, etc.

{:#conclusion}
## 5. Conclusion

Let me recap the questions I have attempted to answer in this article:

* How to transition from SQL to NoSQL if I already have a relational database?
* How to validate documents in CouchDB?
* How to achieve document-level access control?
* How to create an offline-first application using CouchDB/PouchDB?
* How to implement authentication & authorization if I am using PouchDB?
* How to restrict write access in CouchDB?
* How to setup replication if I have many CouchDB databases?
* How to design CouchDB/PouchDB data access layer using Angular/Ionic?

Thank you for reading.