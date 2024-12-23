---
layout: post
title: javaScript
date: 2024-12-02 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# codingTest  

문제

평균보다 큰 숫자 배열로 담아 출력하기

````javascript
//[7,8,10,100,99,44,23,40,14,80]
//평균보다 큰 숫자 배열로 담아 출력
class LargeNum {
	constructor(id) {
    	this.id = id;
        this.avgVal = 0;
        this.lrgVal = null; // []? null?
    }
    avgNum(item){
        item.forEach(v => { this.avgVal += v });
        this.avgVal /= item.length;
    }
    lrgNum(item) {
    	this.lrgVal = item.filter(v=> this.avgVal < v);
    }
    output(){
        let stringOut = ""; 
    	this.lrgVal.sort((a,b)=>a-b);
        stringOut += "[ ";
  		this.lrgVal.forEach((v,i)=>{
        	stringOut += `${v}`;
            (i !== this.lrgVal.length-1) && ( stringOut += ", ");
        });
        stringOut += " ]";
        document.write(stringOut);
    }
    run(item){
    this.avgNum(item);
    this.lrgNum(item);
    this.output();
    }
}
const avgLNum = new LargeNum("avgLNum");
avgLNum.run([7,8,10,100,99,44,23,40,14,80]);
````

