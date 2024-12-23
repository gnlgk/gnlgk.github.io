---
layout: post
title: javaScript
date: 2024-08-04 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 코딩테스트

문제
````
배열안의 유사배열의 같은 인덱스값 가져오기
//zlc
//aod
//rvr
//de
````

풀이
````javascript
  const myA = ['zard',"love","cdr"];
  const zlc = [];
  const aod = [];
  const rvr = [];
  const de = [];

  const ab = myA.map((e,i,a) => a[i][0]);
  document.write(ab);
  document.write("<br>","<br>");
  const b = myA.map(([e1,e2,e3,e4]) => [e4]);
  document.write(b);

  document.write("<br>","<br>");
  for(let key in myA) {
    for(let e in myA[key]) {
      e==0 && zlc.push( myA[key][e] );
      e==1 && aod.push( myA[key][e] );
      e==2 && rvr.push( myA[key][e] );
      e==3 && de.push( myA[key][e] );
    }
  }


  document.write(...zlc , "<br>");
  document.write(...aod , "<br>");
  document.write(...rvr , "<br>");
  document.write(...de , "<br>");
````
````
result[i][j]    myA[i][j]   myB[i][j]
[0][0]          [0][0]      [0][0]
[0][1]          [0][1]      [0][1]
[0][2]          [0][2]      [0][2]
[1][0]          [1][0]      [1][0]
[1][1]          [1][1]      [1][1]
[1][2]          [1][2]      [1][2]
[2][0]          [2][0]      [2][0]
[2][1]          [2][1]      [2][1]
[2][2]          [2][2]      [2][2]
````
