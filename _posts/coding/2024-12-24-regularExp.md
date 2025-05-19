---
layout: post
title: javaScript
date: 2024-12-24 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 정규표현식

@ : 익스케이프 안해도됨, 그냥 씀
'+' : 한 개(1) 또는 여러개
[0-9+] : 숫자 또는 '+'기호
[0-9]+ : 숫자 한개 또는 여러개
'*' : 없거나(0) 또는 여러개
? : 없거나(0) 또는 한 개(1)
    ex > https? : http or https
{} : 구간을 제한할 때 사용
    ex > #[0-9A-Za-z]{6} - 헥사코드, {2,4} - 2번에서 4번까지
    {0,3} - 없거나 3개까지, {3,} - 최소 3개이상

````javascript
const text = ["4/8/17","10-6-2018","2/2/2","01-01-01"];
const rexp = /\d{1,2}[-\/]\d{1,2}[-\/]\d{2,4}/;

let result = text.map((val)=>{
	if(rexp.test(val)){return val};
})
document.write(result);
````

vim에서 +, *, ?, {}(중괄호) 사용 - '\v' 붙이기(vim에서 정규표현식 사용 시)
    ex > /\v\$\d{3}/
/ ? : 위 아래로 이동
/%s/1007/zard/g : 1007을 zard로 변경




````javascript
휴대폰 /01\d[-\/ ]?\d?\d{3}[-\/ ]?\d{4}/
짝수 /^\d*[02468]$/
홀수 /^\d*[13579]$/
=> 입력값을 trim한 상태로 정규식 확인(문자포함인지)
````
trim() - 비파괴 (문자열 중간의 공백은 유지됩니다. 반환만 하기 때문에 원본 문자열은 바뀌지 않습니다)

*, +, {n,}: 같은 메타 문자가 탐욕적(greedy)이므로 가능한 한 가장 큰 덩어리를 찾으려함
*?, +?, {n,}?: 게으른(lazy) 수량자 - 작은 덩어리로 찾아줌

ex > ^cat$ - 줄에 cat만 존재해야됨
문장에 있는 단어 찾기 - \bcat\b 
\b - 단어의 시작과 끝(boundara), 단어의 경계
\B - 단어의 경계와 일치시키고 싶지 않을 때

<!doctype html> 위,앞에는 공백, /n 도 들어갈수 없음

(?m) : 다중행 - 자바스크립트를 포함한 대부분의 정규 표현식 구현에서 지원하지 않는다.
