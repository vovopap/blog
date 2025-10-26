---
layout: post
locale: uz_UZ
title: "Amazon LP savollariga STAR uslubida javob beraman"
---

Bu postda 2021-yilda FAANG behavioral interviewlarga qilgan tayyorgarligimdan qolgan artefactlar bilan ulashaman. Har bir Amazon Leadership Principle (LP) uchun o'zimning tajribamdan kelib chiqib story-chalar yozib chiqqanman. Albatta, interviewga tayyorlanayotgan bo'lsangiz siz ham o'zingiznikini yozib chiqishingiz kerak bo'ladi, bularni namuna uchun ulashyapman. Yana menikini aytib yurmanga :D

Pastda behavioral savollarga javob berilmagan. Aksincha, hokoyalarim Amazon LP bo'yicha kategoriyalangan. Aytgancha, men tayyorlangan vaqtda atiga [12 LP](https://www.amazon.jobs/content/en/our-workplace/leadership-principles) bor edi, hozir o'zgargan bo'lishi mumkin. 

1. [Customer Obsession](#customer-obsession)
1. [Thinking big](#thinking-big)
1. [Ownership](#ownership)
1. [Bias for action](#bias-for-action)
1. [Invent and Simplify](#invent-and-simplify)
1. [Earn trust](#earn-trust)
1. [Are right, a lot](#are-right-a-lot)
1. [Dive Deep](#dive-deep)
1. [Learn and Be Curious](#learn-and-be-curious)
1. [Have backbone; Disagree and Commit](#have-backbone-disagree-and-commit)
1. [Insist on the Highest Standards](#insist-on-the-highest-standards)
1. [Deliver Results](#deliver-results)


{:#customer-obsession}
## Customer Obsession [#](#customer-obsession)
Leaders start with the customer and work backwards. They work rigorously to earn and keep customer trust. Although leaders pay attention to competitors, they obsess over customers.

_Case 1: Five fewer clicks._

|---|---|
| **S** | My manager at KeyPlanSolution was obsessed over customer experience and long proposed implementing drag/drop support in our highly engaged event scheduler. However, the feature previously was dismissed due to technical limitations (our calendar library did not support it out of the box and it was a cross-platform app that needed to work well both in web and tablet devices). |
| **T** | The next time the feature was brought up by the manager, I decided to take on the challenge. |
| **A** | I asked my manager for time to investigate possible solutions. Luckily, I discovered several solutions, each with their own nuances and trade-offs. Unluckily, I needed to choose one. Through judgment and discussions with my team, I finally choose the best solution and implemented/tested/delivered the feature. |
| **R** | Planning an event now takes 5 fewer interactions - thus happy customers. Drag/drop feature became a perfect sales pitch for the young startup. I learned to never dismiss customer needs due to technical complexity. I also gained my manager's trust and respect as a team member who is not afraid of challenges and uncertainties. |

_Case 2: Revamping order history._

| **S** | Usually, as a software engineer, I am not the one who sets the priorities. It is actually the product owner who does it. Well, while working on a bug fix in our order history module I found myself extremely frustrated with every page refresh. The page was taking unreasonably long to load. I thought to myself "If this bugs me, it should definitely be bugging the customers. Through quick investigation of backend and frontend code, I noticed several inefficient parts - probably accumulated over many iterations and feature additions. |
| **T** | So I took the initiative to revamp the page which would speed up the load time by many times. However, I needed to convince my PO to prioritize the revamp. |
| **A** | Before the day I brought up the issue in the daily meeting, I did my homework and listed down potential improvements (like pagination, lazy loading, more efficient DB queries, and smart indexes). I also told the PO estimated load time improvement and approximate story points necessary to complete the revamp. I was able to convince the PO to work on my proposal and we shipped the new version soon after. |
| **R** | We received a positive feedback from customers who seemed to have previously accepted the subpar performance on the page. What did I get? I got satisfaction from my job - knowing the fact that I made a positive impact on our customer's day to day activities. For the development team, it meant a better codebase and less frustration. |

{:#thinking-big}
## Thinking big [#](#thinking-big)
Thinking small is a self-fulfilling prophecy. Leaders create and communicate a bold direction that inspire results. They think differently and look around corners for ways to serve customers.

_Case 1: Moving from standard pages to SPA._

| **S** | Having known the benefits of SPA, a decision to rewrite our Retail CRM system to SPA frontend + REST APIs had been already made. But, we could just never take on it because features were always prioritized. |
| **T** | I did not feel right about writing code that would eventually be rewritten. I also knew as a startup we were not going to take on the rewrite. I had a good idea to have win-win situation here. So, I decided to convince the stakeholders with going hybrid - develop new features on SPA approach. |
| **A** | I did my homework both regarding the benefits and how actually technically we would do. I needed to convince both stakeholders and other team members. I explained that the switch to SPA needed to be done incrementally and we all know we can't just one day drop all feature development and focus on rewrite. I also explained that we could work with Angular modules and incrementally connect modules to one app. |
| **R** | Luckily I got everyone's approval and from there onward we build lightweight Angular modules for new features. And every time an existing feature needed extensive changes, we would rewrite that part in Angular and connect to our SPA architecture. The stakeholders were happy with feature delivery, developers were happy with codebase and low technical debt. |

{:#ownership}
## Ownership [#](#ownership)
Leaders are owners. They think long term and don’t sacrifice long-term value for short-term results. They act on behalf of the entire company, beyond just their own team. They never say “that’s not my job”.

_Case 1: Database migrations rock!_

| **S** | During my employment at OpenReel, my responsibilities were mainly on the frontend side. However, from time to time I would take some tasks on the backend as well. One of those tasks involved modifying our database schema. I naturally searched for schema migration files, but turns out we did not have them. I could simply add my column to database and update relevant entities. But, I did not.. |
| **T** | Having previously used migrations on several projects and knowing their benefits, I decided to integrate it into our development process. |
| **A** | I proposed the idea to my team members and informed them of its benefits. They appreciated the idea and I went on to implement it. After coding it up, I decided to also create a short section in our README file on how to work with migration files locally. |
| **R** | With minimal effort spent, I was able to improve our development cycle. This came very useful especially for new joiners who could have up-to-date database schema with just one command. |

_Case 2: Let's help the Team Leader._

| **S** | I recently had an interesting retrospective event in my current company. In our retros, our Scrum Master usually asks us to write down things under two columns: things we liked during the past weeks and things we did not like. Our team leader wrote down that he is getting more and more away from daily coding due to his other responsibilities such as feature alignment meetings, security activities, and monthly releases. |
| **T** | I thought a little about it and realized we need take on some of his responsibilities. |
| **A** | So I suggested him to delegate some of his tasks to us. He found the suggestion promising and thanked me. |
| **R** | As a result, he recently asked the team for someone to help him in refinement of an upcoming big feature. To that, I readily volunteered. I learned a lot during our refinement sessions. My knowledge later became very crucial in the delivery of the feature because the team leader went on the vacation. I am sure he enjoyed his vacation knowing I would be there to support the team. I learned not to be afraid to speak up and to take ownership. And I hope I earned my team leader's trust and respect with that. |

{:#bias-for-action}
## Bias for action [#](#bias-for-action)
Speed matters in business. Many decisions and actions are reversible and do not need extensive study. We value calculated risk taking.

_Case 1: Maskabor_

| **S** | During the initial outbreak of corona pandemic, much like other countries Uzbekistan also struggled with provision of products such as masks, antiseptic gels and gloves. Me and several of my software engineer friends were stuck in quarantine. We wanted to do something to help the corona situation. |
| **T** | We decided to create a web app to see where those corona products were in stock. |
| **A** | The main issue was the data. Unfortunately, in Uzbekistan there is no central API to read this information. However, this was not going to stop us from taking an action. I proposed to go brute force way - to manually call every pharmacy in Tashkent city and gather our own data. 8-10 ten people divided Tashkent city map into regions and started calling. We knew we couldn't do it forever, but we needed to see if the app is actually needed by people in the first place. |
| **R** | We delivered the service and actually received positive feedback from people with whom we shared it. Unfortunately for our app but fortunately for the people, in the coming days all the stocks were filled and all pharmacy stores had enough products - making our app no longer necessary. However, I learned an important lesson - bias for action. Some things have to be done fast and immediately. I am proud of the project. |

_Case 2: POC done right_

| **S** | During my short internship at Pro7, I had a unique opportunity to work on an Applicant Tracking System for HRM. The company was a small team of 3-4 developers mainly doing freelance work. And the project for which I was hired was a POC app. The stakeholders were trying to come up with a perfect feature set and perfect tech stack for the project. However, I wanted to delivery the app to customers as soon as possible. After all, it is a POC app and we did not even know there is a market for us. |
| **T** | So, I had to convince them to do a minimum viable product and get feedback from customers asap. |
| **A** | I explained to the stakeholders why we should not be thinking much about details and that much of what we do now can be fixed or modified easily. I also explained not to be choosy about tech stack and do it in the technologies we were all comfortable (PHP, MySQL, Apache, and tradition frontend, no SPA). |
| **R** | Fortunately they saw a sense in my proposal and agreed to it. I was able to delivery the project in 1-2 months. The feedback was very useful in setting the direction for the project and we all felt relieved not having done the full feature set. |

{:#invent-and-simplify}
## Invent and Simplify [#](#invent-and-simplify)
Leaders expect and require innovation and invention from their teams and always find way to simplify. They are extremely aware, look for new ideas everywhere, and are not limited by "not invented here".  As we do new things, we accept that we may be misunderstood for long periods of time.

_Case 1: Microservice calls simplified._

| **S** | I recently had a series of feature refinement meetings with my team lead. A certain interaction flow between Microservices has been previously defined by solution architects responsible for the feature. However, I noticed something odd there. Service A is supposed to send an attribute (a key/value pair) to Service B, but Service A needs to call Service B to get that value and Service A did not really use that value - just need to pass on. So, I posed the question: Why should Service A send the value if Service B can readily access it on its own. My team leader seemed to agree on this, but said the decision has been made and to change we needed to re-coordinate with the team responsible for Service B. |
| **T** | I needed to talk with the other team and explain the situation. |
| **A** | So I did it. I set up the call with the other team. Before going into the meeting, I did my homework and gathered my thoughts. I explained the whole situation and presented the solution. |
| **R** | It was a quick realization on their part and they agreed to the change. It was a major win for our team in terms of effort needed to complete that feature. The story points were decreased from 8 to just 3. It was a big relief for our team since we had some tight deadlines there. |

{:#earn-trust}
## Earn trust [#](#earn-trust)
Leaders listen attentively, speak candidly, and treat others respectfully. They are vocally self-critical, even when doing so is awkward or embarrassing. Leaders do not believe their or their team's body odor smells of perfume. They benchmark themselves and their teams against the best.

_Case 1: Earning my team leader's trust and respect. Don't shake the boat you are onboarding._

| **S** | It was my first weeks in my current company. Given the sheer size of the company, I had the most challenging onboarding experience. I had an onboarding buddy, but she couldn't answer all of my questions because she also joined the company few months before. So, I was asking most of my questions from my team leader. He was always helpful and willing to answer all my questions in great details. However, I felt I was disturbing him too much. |
| **T** | So I needed to clear the air regarding this and make sure I am onboarding the team (boat) without shaking the team. |
| **A** | So I did what I always do - talk openly and address the issue. A retrospective meeting is the best place for this. In one of such meetings, I raised the issue. My team leader assured me that I was not disturbing him, but also suggested that I first post my question into team channel and if I don't get a good answer from other team members, then I could approach him. |
| **R** | This way I was able to onboard my team smoothly and positively. I am 100% sure that I was able to earn my team leader's trust and respect because from that time on my connection with my team leader was on the next level. |

{:#are-right-a-lot}
## Are right, a lot [#](#are-right-a-lot)
Leaders are right a lot. They have strong business judgement and good instincts. They seek diverse perspectives and work to disconfirm their beliefs.

_Case 1: CPU playing games on me._

| **S** | You all probably agree with me that the most challenging bugs are the ones which happen inconsistently. In my career, I faced dozens of such bugs. One interesting case was related to video quality bug in online video chat app. We were struggling with it for sometime then and made some fixes that did not entirely solve the issue. I was assigned this pesky bug and was given plenty of time to work on. |
| **T** | The problem was with Browser Media APIs. Specifically, MediaDevices.getUserMedia(). We would pass the desired resolutions and depending on the mood, it would either give us the stream with the right resolution or lower resolution. |
| **A** | I first thought maybe we are getting the right resolution but losing it somehow when displaying or sending it over the network. But those parts were all good. I finally pinned down the issue to MediaDevices.getUserMedia() API. So, having no clue I mindlessly refresh the page multiple times. And it hits me that I get lower resolution when my CPU fan is working hard, and get the right resolution when it is quiet. I said "hmmm it can't be true" So I did some research on that and it turns out that Chrome indeed controls the resolution based on the current available CPU and completely disregards your resolution parameters. |
| **R** | I think the situations like these sharpen your instincts and judgement. Needless to say, there was not a clear-cut solution. We did our best with achieving the highest resolution possible. Instead, we channeled our efforts to making the whole app CPU efficient. |

{:#dive-deep}
## Dive Deep [#](#dive-deep)
Leaders operate at all levels, stay connected to the details, audit frequently, and are skeptical when metrics and anecdote differ. No task is beneath them.

_Case 1: Going beyond coding at Swisscom._

| **S** | In my current team, I had a unique experience of extending myself beyond coding. In my team, we praise ourselves as T-shaped engineers who are responsible for end-to-end delivery of features. While each of us has a certain expertise, we are also well-equipped to work at all levels. |
| **T** | In the DevOps spirit, I also needed to become a T-shaped engineer. |
| **A** | For that, all I needed was a little bit courage every time an opportunity was presented. In one occasion, I was a full-time tester for a week. I learned how to clearly & thoroughly present my findings from testing activities. I was an interim Scrum Master for a week, where I was leading daily meetings and supporting the team from Scrum Master perspective. I am also contributing to hiring process with technical interviews. |
| **R** | I can't say I am already a T-shaped engineer, because there are still areas of software development I need to gain knowledge such as security, cloud-native computing, and solution architecture. But, I have learned a lot throughout this journey and was exposed to different perspectives to software development. |

{:#learn-and-be-curious}
## Learn and Be Curious [#](#learn-and-be-curious)
Leaders are never done learning and always seek to improve themselves. They are curious about new possibilities and act to explore them.

_Case 1: Discovering the world of Electron.js_

| **S** | During my trial period in Openreel, I was asked to develop a screen annotation. I was very surprised - how could a web developer build an app that draws on the whole user screen? That has to be at least a desktop app, I thought. The only think I was given was a link to a technology called Electron.js. |
| **T** | So I needed to somehow build the app using Electron.js. |
| **A** | I started reading the documentation and several articles about it. I was shocked to learn that my favorite apps like Slack and Visual Studio Code were built on top of it. And the idea of web code reaching out to client's Operating System through Node.JS was crazy. |
| **R** | In those two weeks, I learned so much new things and opened a new world for myself. And actually I was able to complete the task and got positive feedback from my trial period. |

{:#have-backbone-disagree-and-commit}
## Have backbone; Disagree and Commit [#](#have-backbone-disagree-and-commit)
Leaders are obligated to respectfully challenge decisions when they disagree, even when doing so is uncomfortable or exhausting. Leaders have conviction and are tenacious. They do not compromise for the sake of social cohesion. Once a decision is determined, they commit wholly.

_Case 1: Moving from standard pages to SPA._

| **S** | Having known the benefits of SPA, a decision to rewrite our Retail CRM system to SPA frontend + REST APIs had been already made. But, we could just never take on it because features were always prioritized. |
| **T** | I did not feel right about writing code that would eventually be rewritten. I also knew as a startup we were not going to take on the rewrite. I had a good idea to have win-win situation here. So, I decided to convince the stakeholders with going hybrid - develop new features on SPA approach. |
| **A** | I did my homework both regarding the benefits and how actually technically we would do. I needed to convince both stakeholders and other team members. I explained that the switch to SPA needed to be done incrementally and we all know we can't just one day drop all feature development and focus on rewrite. I also explained that we could work with Angular modules and incrementally connect modules to one app. |
| **R** | Luckily I got everyone's approval and from there onward we build lightweight Angular modules for new features. And every time an existing feature needed extensive changes, we would rewrite that part in Angular and connect to our SPA architecture. The stakeholders were happy with feature delivery, developers were happy with codebase and low technical debt. |

{:#insist-on-the-highest-standards}
## Insist on the Highest Standards [#](#insist-on-the-highest-standards)
Leaders have relentlessly high standards — many people may think these standards are unreasonably high. Leaders are continually raising the bar and driving their teams to deliver high quality products, services and processes. Leaders ensure that defects do not get sent down the line and that problems are fixed so they stay fixes.

_Case 1: When RESTful APIs aren't really RESTful_

| **S** | As a developer, it really bothers me when http verbs are misused. Especially, when GETting a resource is done via a POST request. In OpenReel, I was mainly working as a frontend developer consuming backend endpoints which did not seem to follow any rules whatsoever: no api versioning, no following http verbs and response statuses. |
| **T** | I definitely could not work in such environment. Besides, these backend developers were rewriting the apis from the old version. If there was any good moment to avert future issues, it was then. |
| **A** | As usual I did my homework and presented facts to the team. I proposed to set certain standards as to our APIs —  specifically, to follow RESTful framework. The team agreed with the proposal. To assure that we were following these rules and delivering high quality APIs, it was decided that at least two need developers to approve PRs before they can be merged. |
| **R** | Thanks to those changes, not only did we end up having consistent backend codebase, but also clean and highly-readable frontend codebase. Sure, we probably now spent twice more time for developing endpoints, but the benefits are definitely worth it. |

_Case 2: The tale of a tab! OR Where did these 4 spaces come from?_

| **S** | During my employment in KeyPlanSolution, I was working on a feature which involved both frontend and backend. Our frontend consumed data from the backend in JSON format. When making a call from frontend, I kept getting parse exception. I look at the data and all seem fine. After some debugging, I noticed some empty spaces at the start of JSON response. I was very surprised to see that and immediately jumped to backend code to find the issue. I spend some time there, but everything was fine. I was doing standard stuff and using standard components and services of our MVC-based php framework. I asked help from my coworker who has been in the team long before me. Before I could finish describing the issue, he told he knows that issue for some time now and that he couldn't track down the issue. So he would trim the response before parsing. The workaround was used in dozens of places in frontend code and smelled really bad. |
| **T** | I just could not work around the issue and add to the bad code. I decided to track down the issue. |
| **A** | It meant going deep into framework code. PHP is not so famous for debugging. First I  tried putting echo statements in different places, no luck. Then, I decided comparing my problematic API with good API. I spend a whole day on this. I finally found the issue the next day. If you worked with PHP, you know that every php script file starts with <?php. In one of our model files, someone accidentally hit tab in the beginning. And apparently, this is included in the final response every time some API uses this model. All I needed to do was to remove this tab. I also removed workaround code in frontend. |
| **R** | My bug hunting effort now improved our codebase and avoided future frustration by other developers. |

{:#deliver-results}
## Deliver Results [#](#deliver-results)
Leaders focus on the key inputs for their business and deliver them with the right quality and in a timely fashion. Despite setbacks, they rise to the occasion and never settle.

_Case 1: KuralBook — delivering the first version on time._

| **S** | In 2020, I was working with a client to develop a cross-platform mobile application. We already planned the stories for the first version of the app and the deadline was set. After working for the next two weeks, I identified certain design gaps which clearly risked delivering the 1st version by the deadline. |
| **T** | The challenge was to somehow deliver it by the deadline. |
| **A** | First I thought of working overtime on the project and deliver it no matter how. But, even with overtime there was not any guarantee I would make it on time. Instead, I decided to come clear with the client and explain the situation. I thoroughly explained the issues that came up and laid out possible solutions to the replanning. One, which client did not like much, was to postpone the deadline. The other option was to reconsider the feature set for the first version. The client agreed on it and we started dividing stories into must-haves and good-to-haves. |
| **R** | The deadline was met. I committed extra time on the project, but not much that it would affect my work-life balance. I delivered all the must-have features + 50% of good-to-have features. Situations like this taught me to keep accurate expectations and be always transparent about the progress. |
