---
layout: post
title: javaScript
date: 2024-08-05 14:00 +0900
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
배열의 누적값 만들기
//[1,3,6,10,15]
````

풀이
````javascript
  const cumulativeSum = {
	  myA : [1,2,3,4,5],
    cumulative : [],
    run : function(){
        for(let i=0;i<this.myA.length;i++) {
          this.cumulative[i] = 0;
          for(let j=0;j<=i;j++) {
              this.cumulative[i] += this.myA[j];
          }
        }

      document.write(String(this.cumulative));
    }
  }
cumulativeSum.run();
````

````
i   j   myA[j]    cumulative[i]
0   0   1         1
1   0   1         1
1   1   +2        3
2   0   1         1
2   1   +2        3
2   2   +3        6
3   0   1         1
3   1   +2        3
3   2   +3        6
3   3   +4        10  
4   0   1         1
4   1   +2        3
4   2   +3        6
4   3   +4        10
4   4   +5        15
````
