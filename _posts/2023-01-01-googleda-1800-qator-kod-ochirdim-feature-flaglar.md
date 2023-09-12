---
layout: post
locale: en_US
title: "Googleda 1800 qator kod o’chirdim: feature flaglar"
---

![Feature flags](/assets/feature-flags.jpg)

Dasturlashda menga yoqadigan ishlardan biri bu kod o’chirish. Bugun 1850ta qator kod o’chirgani katta pull request yaratdim 😇

Aslida eng zo’r kod bu yozilmagan kod. Chunki qancha readable yoki qancha robust qilib yozilmasin, kod baribir kod. Uni maintain qilish kerak. Shuning uchun har bir qo’shilayotgan kodni review paytida “shu bizga kerakmi?” degan savol ostiga tashlanadi.

— O’zi qanday qilib 1850ta qator kodni o’chirishga haddingiz sig’di? Shuncha kod bekordan-bekor yotmagandir?

Yaxshi savol! Feature flaglar haqida eshitganmisiz? Agar siz buni nimaligini bilsangiz, tepadagi savollarga javobni bilsangiz kerak.

Feature flag bu mavjud bo’lgan bir funksionalni yoqish yoki o’chirib turish uchun ishlatiladi. Feature flaglar iterative software development uchun juda muhim bo’lib har xil xolatlarda ishlatiladi. 

Juda oddiy misol. Deylik, Twitter yangi `Verified` degan featureni foydalanuvchilarga chiqarmoqchi. Uni `isVerifiedFeatureEnabled` degan flag ostida chiqarishadi. Bu flagni qiymatini maxsus servisdan o’qib kelishadi. Agar, jiddiy bir bug topilsa shu flagni qiymatini `false` ga o’zgartirib qo’yishadi. Hammasi eski xolga qaytadi.

Bugni darxol tuzatishsa ham bo’ladi, lekin unga ko’p vaqt ketadi. Twitter darajasidagi kompaniyalar uchun sekundlar ⏳ millionlarga teng💰.

Meni xolatimda mavjud funksionalni re-design qilish kerak edi. Yangi yechim tayyor bo’lib uni puxta test qilganimizdan keyin, feature flagni productionda yoqdik. Yangi kod ishlashiga amin bo’lmaginimizgacha eski kod joyida turadi. Keyin, o’chirib tashlasak bo’ladi.

Osha 1800 qator kod bu eski funksional edi.