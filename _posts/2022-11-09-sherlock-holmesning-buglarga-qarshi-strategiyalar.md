---
layout: post
locale: en_US
title: "Sherlock Holmes'ning buglarga qarshi strategiyalari"
description: "Bu blog postda buglarni yechish strategiyalari haqida gaplashamiz."
tags: ["Dasturlash", "Bug", "Buglar bilan ishlash", "Software engineering", "Kodlash"]
---

Menga “bug” lar bilan ishlash juda yoqadi. Ayniqsa ayyor buglarni ustida ishlasam o’zimni Sherlock Holmes yoki Dr. House dek his qilaman.

Dasturlashni yangi o’rganayotganlar uchun bu uncha zavqli narsa emas, bilaman. Shunga bugun buglarni adabini berish strategiyalari haqida gaplashamiz. Kettik!

**Error messageni o’qi, ey inson!**

90% xolatda error messageni o’zi muammoni aytib turadi. Lekin biz negadir boshqa joyga qarab ketamiz. Bir paytlar men ham shunaqa qilardim. Error messageni o’qib uni tushunishga harakat qiling.

**5ta nega (5 whys).**

Error message sizga muammoni topib bermagan xolda u kalavani uchi bo’ladi. Shu errordan boshlab o’zingizdan besh marta “nega?” deb so’rasangiz asosiy muammoga yetib borasiz. Masalan, deylik meni java kodimda NullPointerException tashayapti:

 1. Nega NullPointerException tashayapti? — Chunki “Date myDate” nullga teng.
 2. Nega myDate nullga teng? — Xaa, #setDate metodi chaqirilmayapti shekili.
 3. Nega #setDate chaqirilmayapti? — Hmm, #setDate’ni for-loopni ichida chaqirgandim. Balki for-loop to’g’ri ishlamayapgandir.
 4. Nega for-loop ishlamayapti? — Ehh, qovun kalla i > list.size() emas i < list.size() bo’ladiku!!!
 5. …

**Kodingiz ishlamasa, dardingizni kimga aytasiz?**

Dadangizga, oyangizga, o’rtog’ingizga, itingizga, mushugingizga, hattoki rezinali o’rdakga aytsangiz bo’ladi. Behazil. Biror kishiga bugingiz haqida aytib bersangiz, muammoni yechimi birdan kallangizga kelib qolishi shansi katta. U odam dasturlashni bilishi shart emas. Kimga gapirib berishingizdan qattiy nazar, quyidagilarni aytib bering:

 1. O’zi nima bo’lyapti?
 2. Nimadan keyin shunaqa bo’lyapti?
 3. Uni to’g’irlash uchun nimalar qilib ko’rdingiz?
 4. Yana nimalardan shubxangiz bor?

**Chalg’ing.**

O’shanda ham javobni topa olmasangiz va juda boshingiz qotgan bo’lsa, chalg’ing. Boshqa ishga o’ting, kofe/choy break oling, yoki tashqariga bir aylanib keling. 1-2 soatdan keyin yoki 1 kundan keyin (agar shoshilinch bo’lmasa) yana bir harakat qilib ko’ring. Ko’p xolatda muammoga svejiy kalla bilan qarash muammoni ildizi topshiga yordam beradi. Bingo! — deysiz keyin.

**Sheriklardan yordam so’rang.**

Aslida yordam so’rash ohirida umuman iloji bo’lmaganda qilinishi kerak emas. Lekin negadir bazida biz yordam so’rashni o’zimizga erk deb bilmaymiz. Men uzimni eslayman. Soatlab qiynalib umuman kallam qotib qolgandan keyin yordam so’rardim. Hozir esa, bez betdek team leaderimni oldiga boraveraman.