---
layout: post
locale: en_US
title: "Acceptance Criteria haqida"
---

Kelinglar bugun Acceptance Criteria haqida gaplashamiz. Nega bugun? Chunki bugun shu mavzuga oid bir foydali [artikl](https://brettsbabble.wordpress.com/2011/03/26/patterns-for-effective-acceptance-criteria/) o’qidim :D. Tushunishni eng yaxshi yo’li tushuntirish deganlaridek, bugun sizlarga Acceptance Criteria bo’yicha oz-moz bilimimni ulashaman. Kettik!

**Acceptance Criteria o’zi nima?**

Acceptance Criteria bu bir featureni yakunlash uchun shartlar. U oddiy technical bilimga ega bo’lmagan odam uchun ham tushinarli tilda yoziladi va technical dunyo (Software Engineer, QA) va non-technical dunyoni (Project Manager, Project/Product Owner) bog’lab turadi. Shuning uchun ham Acceptance Criteria Software Developmentda muhim ro’l o’ynaydi.

Yaxshi Acceptance Criteria yangi featurelarni osonlik va o’z vaqtida yetkazib berishga yordam beradi. Yomon Acceptance Criteria esa yangi featurelarni yetkazib berishda qiyinchiliklar, xatoliklar, tushunmovchiliklar, kechikishlar va asab buzarchilikarga olib boradi.


**Acceptance Criteria qanday yoziladi?.**

Acceptance criteria asosan Given.. When.. Then strukturasida yoziladi. “Talk is cheap, show me the code” deganlaridek, kelinglar bir-ikkita misollar keltiramiz.

_Example A: Login with email and password_
```
Given: that user has already signed up
And: their account is active
When: they input their email and password correctly
And: click Login button
Then: they should be authenticated
And: navigated to the home page
```
_Example B: Add product to cart without being logged in._
```
Given: that user is not logged in
And: is in product detail page
When: they click “Add to cart” button
Then: the button text changes to “Added to cart”
And: the button is disabled
```

**Acceptance Criteria bilan oddiy feature descriptionni farqi nimada?.**

Formatdan tashqari boshqa katta farqi yo’q. Acceptance Criteria feature descriptionga qaraganda ancha batafsil bo’ladi.

**Acceptance Criteria Software Engineerlar uchun kerakmi?**

Feature requestlar biznes tarafdan kelgani uchun asosan Acceptance Criteriani Product Owner va Project Managerlar yozishadi. Lekin sog’lom komandalarda Software Engineerlar ham bu jarayonda aktiv qatnashishadi. Shu orqali ko’p detallar oldindan kelishib olinadi va tushinmovchiliklarni oldi olinadi.

Bu jarayonda Software Engineerlar qatnashishi uchun yana bir sabab bor. Bu Test-Driven Development (TDD). Agar komanda TDD qilsa, Acceptance Criteriadagi har bir shart keyinchalik unit test yoki end-to-end testga tarjima qilinadi. Shu sababli Acceptance Criteriada dasturchilar qatnashishsa testlar yozish ossonlashadi.

**Qanday qilib Acceptance Criteria yozish skillarini kuchaytirsa bo’ladi?**

Albatta, ko’proq Acceptance Criteria yozishda qatnashish orqali. Tepadagi linkda ham bir talay maslahatlar berilgan — o’qib chiqing.