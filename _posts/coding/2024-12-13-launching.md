---
layout: post
title: javaScript
date: 2024-12-13 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 진수  

## 표현방식

자바스크립트는 모든 숫자를 부동소수점으로 처리하여 처리가 느림
````
고정소수점      부동소수점             컴퓨터
0.1234  === 0.001234 * 10²      === 0.001234e2
        === 0.01234 * 10¹       === 0.01234e1
        === 0.1234 * 10⁰        === 0.1234e0
        === 1.234 * 10⁻¹        === 1.234e-1
        === 12.34 * 10⁻²        === 12.34e-2
````

## 진수변환
````javascript
// Prefix - 앞에 +23
// Postfix - 뒤에 23+
let myB = 0b0101010;
let myO = 012312;
let myV = 1231;
let myH = 0x421;

document.write(myB +"<br>"); // 기본 출력은 10진수
document.write(myO +"<br>");
document.write(myV +"<br>");
document.write(myH +"<br>");

document.write(myB.toString(2) +"<br>");
document.write(myO.toString(8) +"<br>");
document.write(myV.toString() +"<br>");
document.write(myH.toString(16) +"<br>");

document.write((myH + myO).toString(2) +"<br>");
````

kernel
shell

