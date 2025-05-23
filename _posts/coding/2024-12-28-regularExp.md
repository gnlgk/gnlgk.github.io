---
layout: post
title: javaScript
date: 2024-12-28 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 정규표현식

() : 표현식 묶어주기
| : or

\1: 앞에서 첫번째로 검출된 단어! 한번 더(역참조)
\2: 두번째 ,\3: 세번째..

자바와 파이썬은 group이라는 이름의 배열이 포함된 결과 객체(match object)를 반환

````javascript
const html=`<h1>awdw</h2>`
let rexp = /<[hH]([1-6])>.*?<[hH]\1>/;

document.write(rexp.test(html));
````

특수문자(@#$!)하나이상 숫자 1자이상 대문자 1자이상 알파벳으로 구성된 길이 8~15의 비밀번호 정규식
/^.?[@#\$!]+\d+[A-Z]+.{8,15}$/

exec, test, match, replace, search, split등에 정규표현식 사용가능

exec 배열로 반환
match 찾고자하는 문자가 있는지
replace 찾아서 교체
search 찾았을때의 인덱스번호 반환
split 기준으로 분리

````javascript
const targetStr = "This is a pen";
const regexr = /is/ig;

console.log(regexr.exec(targetStr));
console.log(regexr.test(targetStr));
console.log(targetStr.match(regexr));
console.log(targetStr.replace(regexr,"IS"));
console.log(targetStr.search(regexr));
console.log(targetStr.split(regexr));
````

````javascript
const targetStr = "Is this all there is?";
let regexr = /is/;

console.log(targetStr.match(regexr)); // exec처럼 배열로 반환

regexr = /is/ig;

console.log(targetStr.match(regexr));
console.log(targetStr.match(regexr).length)
````

