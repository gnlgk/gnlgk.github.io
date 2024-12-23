---
layout: post
title: javaScript
date: 2024-08-03 14:00 +0900
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
이차원배열의 합(차) 구하기
// [10,10,10]
// [10,10,10]
// [10,10,10]
````

풀이
````javascript
   const twoDimensionalArray = {
    myA : [
      [1,2,3],
      [4,5,6],
      [7,8,9],
    ],
    myB : [
      [9,8,7],
      [6,5,4],
      [3,2,1],
    ],
    result : [],
    run : function(){
      	for(let i=0;i<this.myA.length;i++) {
          this.result.push([]);
          for(let j=0;j<this.myA[0].length;j++) {
              this.result[i][j] = this.myA[i][j] + this.myB[i][j];
          }
     	}
     	console.log(this.result);
    }
  }

  twoDimensionalArray.run();
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
