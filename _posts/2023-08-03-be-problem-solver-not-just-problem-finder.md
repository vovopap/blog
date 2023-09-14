---
layout: post
locale: uz_UZ
title: "Be a problem solver, not just a problem finder"
---

Keling sizga Googleda bo’lgan bir qiziq voqeani aytib beraman. Bir piyola ko’k choy bilan zo'r ketadigan post 🙂 

Googledagi ishimni birinchi 6 oyida komandada tashabbus ko’rsatish muhimligini tushunib yetdim. Yaniy, yangi featurelarni oldinga surish, kunlik ishni sekinlashtirayotgan muammolarni yuzaga olib chiqish, va o’zingiz o’rgangan narsalarni komanda bilan ulashish sizni yaxshi team-player qiladi.

Shu ruhda men ham komandadagi muammolarni yuzaga chiqarishni boshladim. Bir kuni kimdir loglarimizga yangi log line qo’shibdi: PING_REQUEST degan. U log har sekundda yozilib hamma yoqni spam qilib yubordi. Bu production uchun katta muammo bo’lmasada, kunlik ishni beliga yaxshigina tepayotgan eda.

Men shuni daily meetingda o’rtaga tashadim. “PING_REQUEST log har sekundda yozilyapti, ishimizni sekinlashtiryapti. Shuni fix qilishimiz kerak.” dedim. Hammma “Ha..ha.. to’g’ri, fix qilishimiz kerak. Uni throttle qilsa bo’ladi” dedi.

Usha kuni PING_REQUEST kun bo’yi jonimga tegdi. Ertasiga yana dailyda o’rtaga tashadim. “PING_REQUEST log jonga tegyapti. Qanday throttle qilsak bo’ladi? Logging servisimizda shunday feature bormi?” dedim. Team leaderim esa “Bugun ertalab fix qilib qo’ydim, pull qilsang fix keladi senga ham” dedi.

Emotional damage!!! Shu vaziyat menga qattiq tasir qildi. Aslida men nima qilishim kerak edi?

— Muammo borligini anglab yetaman: spam PING_REQUEST log boshqa loglarni o’qigani halaqit qilyapti
— Uni qanday fix qilishni research qilaman: Logging servisda throttle feature borligini qidirib topaman yoki boshqalardan to’g’ridan-to’g’ri yordam so’rayman
— Mavjud yechimlarni ko’rib chiqqaman
— Optimal yechimni kodini yozib code reviewga jo’nataman
— Ertasiga daily meetingda tepadagi qilgan ishlarimni so’ylab beraman

Lesson learned: be a problem solver, not just a problem finder.