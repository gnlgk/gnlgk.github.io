---
layout: post
title: javaScript
date: 2024-08-06 14:00 +0900
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
마름모 별찍기
````

풀이
````javascript
<script>
  for(let i=0;i<10;i++){
    for(let j=0;j<10;j++) {
      if(j>=4-i && j<=5+i && j+5>=i && j+i<=14){
        document.write("*");
      }else{
        document.write("-");
      }
    }
    document.write("<br>");
  }
</script>
````

````
----**----
---****---
--******--
-********-
**********
**********
-********-
--******--
---****---
----**----
````
