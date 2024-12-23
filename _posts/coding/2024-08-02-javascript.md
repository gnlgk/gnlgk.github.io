---
layout: post
title: javaScript
date: 2024-08-02 14:00 +0900
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
// 1,5,9,13,8
// 1,대각선합,대각선합,대각선합,8
````

풀이
````javascript
  const diagonalSum = {
    myA : [1,3,5,7],
    myB : [2,4,6,8],
    result : [],
    run : function(){
      	for(let i=0;i<=this.myA.length;i++) {

          const a = this.myA[i] == undefined ? 0:this.myA[i];
          const b = this.myB[i-1] == undefined ? 0:this.myB[i-1];

          this.result[i]= a+b;
      	}
      	document.write(this.result);
    	}
  }
  diagonalSum.run();
````

i   a   b   result
0   1   0   1
1   3   2   5
2   5   4   9
3   7   6   13
4   0   8   8
