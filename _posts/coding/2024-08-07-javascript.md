---
layout: post
title: javaScript
date: 2024-08-07 14:00 +0900
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
배열의 합 구하기
//8
//8
//8
//4
````

풀이
````javascript
<script>
const myA = [1,2,3,4,5,6,7];

const re=[];
const result=[];

if(myA.length % 2 == 1){
	const n = myA.splice(Math.floor(myA.length/2),1);
    for(let i=0;i<myA.length;i++) {
        for(let j=0;j<=i;j++) {
            if(i+j==(myA.length-1)) { 
              re.push(myA[i]+myA[j]);
            }
        }
    }
    re.push(n);
}
document.write(String(re)+"<br>"); 

</script>
````

````
// myA[0]+myA[6]
// myA[1]+myA[5]
// myA[2]+myA[4]
// myA[3]
````
