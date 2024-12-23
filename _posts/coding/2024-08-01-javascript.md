---
layout: post
title: javaScript
date: 2024-08-01 14:00 +0900
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
대각선 합 구하기
//30+90
//40+80
//50+70
조건: myA,myB 배열갯수같음
````

풀이
````javascript
const reverseSum={
  myA : [30,40,50],
  myB : [70,80,90],
  sum : 0,
  run : function(){
    for(let a in this.myA){
      for(let b in this.myB){
          if(Number(a)+Number(b) == this.myA.length - 1){
            document.write(String(this.myA[a])+"+"+String(this.myB[b])+"<br>");
        }
      }
    }
  }
}

reverseSum.run();
````

a   b   myA.length - 1
0   2   2
1   1   2
2   0   2
