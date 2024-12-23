---
layout: post
title: javaScript
date: 2024-08-08 14:00 +0900
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
행렬의 곱 구하기
[
    [21,18],
    [66,57],
]
````

풀이
````javascript
<script>
const matrixProduct = {
  myA : [
    [1,2],
    [4,5],
  ],

  myB : [
    [9,8],
    [6,5],
  ],

  result : [],

  run : function(){
          for(let i=0;i<this.myA.length;i++) {
            this.result.push([]);
            for(let j=0;j<this.myA[i].length;j++) {
                let sum = 0;
                for(let k=0;k<this.myB.length;k++) {
                    sum += this.myA[i][k] * this.myB[k][j];
                    this.result[i][j] = sum;
                }       
              }
          }
          document.write(String(this.result));
      }
}

matrixProduct.run()

</script>

````

````
[
  [ myA[0][0]*myB[0][0]+myA[0][1]*myB[1][0] , myA[0][0]*myB[0][1]+myA[0][1]*myB[1][1] ],
  [ myA[1][0]*myB[0][0]+myA[1][1]*myB[1][0] , myA[1][0]*myB[0][1]+myA[1][1]*myB[1][1] ]
]
//result[i][j] += this.myA[i][k] * this.myB[k][j];
````
