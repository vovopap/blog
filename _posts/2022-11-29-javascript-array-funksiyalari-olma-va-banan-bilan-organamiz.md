---
layout: post
locale: en_US
title: "Olma va banan bilan JavaScript Array funksiyalarini o'rganamiz"
description: "Bu postda JavaScript Array funksiyalarini iloji boricha osson ko'rinishda tushuntirishga harakat qilaman."
tags: ["JavaScript", "Array", "Funksiya", "Software engineering", "Kodlash"]
---

Menga nafaqat Java, balki JavaScript ham juda yoqadi. Ayniqsa [JavaScriptni Array funksiyalari](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) chotkiy ishlaydi chunki ular juda oddiy va tushinarli yozilgan. Shunchalik oddiy yozilgan-ki xattoki ularni 3ta olma va 2ta banan bilan tushunib olsa bo’ladi :)

Qanday deysizmi? Kettik!

## Boolean funksiyalar

Array.prototype.every()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.every(meva => meva == '🍏') // false
```

Array.prototype.includes()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.includes('🍏') // true 
mevalar.includes('🍓') // false
```

Array.prototype.some()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.some(meva => meva == '🍌') // true
mevalar.some(meva => meva == '🍓') // false
```

**Qidirish funksiyalari**

Array.prototype.at()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.at(1) // '🍌'
```

Array.prototype.findIndex()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.findIndex(meva => meva == '🍌') // 1
```

Array.prototype.findLastIndex()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.findLastIndex(meva => meva == '🍌') // 4
```

Array.prototype.indexOf()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.indexOf('🍌') // 1
```

Array.prototype.lastIndexOf()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.lastIndexOf('🍌') // 4
```

Array.prototype.find()
```
const mevalar = [
  { nom: '🍏', narx: 5 },
  { nom: '🍌', narx: 7 },
  { nom: '🍓', narx: 3 }]
mevalar.find(meva => meva.narx < 6) // { nom: '🍏’, narx: 5 }
```

Array.prototype.findLast()
```
const mevalar = [
  { nom: '🍏', narx: 5 },
  { nom: '🍌', narx: 7 },
  { nom: '🍓', narx: 3 }]
mevalar.findLast(meva => meva.narx < 6) // { nom: '🍓', narx: 3 }
```

## Transformatsiya funksiyalari

Array.prototype.concat()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.concat(['🍏', '🍌']) // ['🍏', '🍌', '🍏', '🍏', '🍌', '🍏', '🍌']
```

Array.prototype.fill()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.fill('🍌', 0, 3) // ['🍌', '🍌', '🍌', '🍏', '🍌']
```

Array.prototype.join()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.join('_') // '🍏_🍌_🍏_🍏_🍌'
```

Array.prototype.reverse()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.reverse() // ['🍌', '🍏', '🍏', '🍌', '🍏']
```

Array.prototype.slice()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.slice(1, 4) // ['🍌', '🍏', '🍏']
```

Array.prototype.pop()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.pop() // '🍌'
console.log(mevalar) // ['🍏', '🍌', '🍏', '🍏']
```

Array.prototype.push()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.push('🍌') // 6
console.log(mevalar) // ['🍏', '🍌', '🍏', '🍏', '🍌', '🍌']
```

Array.prototype.shift()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.shift() // '🍏'
console.log(mevalar) // ['🍌', '🍏', '🍏', '🍌']
```

Array.prototype.unshift()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.unshift('🍌', '🍌') // 7
console.log(mevalar) // ['🍌', '🍌', '🍏', '🍌', '🍏', '🍏', '🍌']
```

## Va boshqa funksiyalar

Array.prototype.forEach()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.forEach(meva => console.log(meva))
// '🍏'
// '🍌'
// '🍏'
// '🍏'
// '🍌'
```

Array.prototype.map()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.map(meva => meva + meva) // ['🍏🍏', '🍌🍌', '🍏🍏', '🍏🍏', '🍌🍌']
```

Array.prototype.filter()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.filter(meva => meva == '🍏') // ['🍏', '🍏', '🍏']
```

Array.prototype.sort()
```
const mevalar = ['🍏', '🍌', '🍏', '🍏', '🍌']
mevalar.sort() // ['🍌', '🍌', '🍏', '🍏', '🍏']
```

Array.prototype.flat()
```
const mevalar = ['🍏', '🍌', [‘🍏', '🍏', '🍌’]]
mevalar.flat()
>> ['🍏', '🍌', '🍏', '🍏', '🍌']
```

Array.prototype.reduce()
```
const mevalar = [
  { nom: '🍏', narx: 5 },
  { nom: '🍌', narx: 7 },
  { nom: '🍓', narx: 3 }]
mevalar.reduce((nomlar, meva) => nomlar + meva.nom, 'mevalar:')
>> 'mevalar:🍏🍌🍓'
```