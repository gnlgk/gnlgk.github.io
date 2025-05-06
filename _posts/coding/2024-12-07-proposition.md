---
layout: post
title: javaScript
date: 2024-12-06 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 자바스크립트 기초   

## 명제와 논리

명제(Proposition)
- 객관적인 기준으로 진릿값을 구분할 수 있는 문장이나 수식
ex > 대한민국의 수도는 서울특별시이다.(true) /  1 + 1 = 3(False)

무한에 가능한 카운트 값은 범위를 정해서 구하면 가능
ex > 별의 갯수

## 논리연산자

수학에서 부정 표기 => ¬p / ˜p / p'

AND(&&) = p ∧ q (논리곱)
OR(||) = p ∨ q (논리합)
Exclusive OR(배타적 OR) - 둘 중 하나만 참일때 참(javascript에서는 사용안함)

p⊕q = ((¬p∧q) ∨ (p∧¬q)) -> javascript에서 Exclusive OR를 구할때 사용

NAND - AND NOT 
NOR - OR NOT
NXOR - XOR NOT
(참조 : 논리회로)

## 명제
동치 - 두 문장이 논리적으로 같다는 것을 의미 
합성명제(Compound Proposition) - 하나 이상의 명제들이 논리연산자에 의해 결합된 명제
항진명제(Tautology) - 결과값이 항상 참인 명제
모순명제(Contradiction) - 결과값이 항상 거짓인 명제
사건명제(Contingency) - 항진명제도 모순명제도 아닌 합성명제

````javascript
const p = [true, false];
const t = [true, true];
const result = [];
// p || q
for(let i=0;i<p.length;i++) {
	result.push( p[i] || t[i] );
}

for(let i=0;i<result.length;i++) {
document.write((p[i]?"T":"F") + "&#x2228;" + (t[i] ?"T":"F" )+ " = " + (result[i]?"T":"F") + "<br>");
}
// 유니코드 html에서 사용하는 법: "&#x2227;"
````

````html
<button id="okBtn">OK</button>
<button id="ccBtn">Cancle</button>
<input id="inputText" type="text">
<script>
//document.getElementById("okBtn").onclick = function() {
//	alert(1);
//}

//document.getElementById("okBtn").addEventListener("click",(e)=>{
//	alert(e.target.id);
//}) // 낱개로 다 적어야됨

addEventListener(
	"mouseover",
	(e)=>{  				//구버전 (e?e:event)
	switch(e.target.id){
    	case "okBtn": 
        	alert(1);
            break;
        case "ccBtn":
        	alert(2);
            break;
        case "inputText":
        	e.target.style.backgroundColor = "gold";
            break;
    }
}); // 통합해서 정리
</script>
````

마우스 이벤트

* click : 요소에 마우스를 클릭했을 때
* dbclick : 요소에 마우스를 더블클릭했을 때
* mouseover : 요소 위로 마우스를 움직였을 때
* mouseout : 요소 바깥으로 마우스를 움직였을 때
* mousedown : 마우스를 누르고 있을 때
* mouseup : 눌렀던 마우스 버튼을 땔 때
* mousemove : 마우스를 움직였을 때
* contextmenu : 마우스 오른쪽 버튼 눌렀을 때 나오는 메뉴가 나오기 전에 이벤트 발생

키보드 이벤트

* keydown : 키를 처음 눌렀을 때
* keyup : 키를 떼었을 때
* keypress : 키를 누른 상태에서

UI 이벤트

* load : 웹 페이지의 로드가 완료되었을 때
* unload : 웹 페이지가 언로드될 때
* error : 브라우저가 자바스크립트 오류를 만났거나, 요청한 자원이 없는 경우
* resize : 브라우저 창 크기를 조정했을 때
* scroll : 사용자가 페이지를 위아래로 스크롤할 때
* abort : 이미지의 로딩이 중단되었을 때

폼이벤트

* input : <input>,<textarea> 요소 값이 변경되었을 때
* change : 선택 상자, 체크박스, 라디어 버튼의 상태가 변경되었을 때
* submit : 사용자가 버튼키를 이용해 폼을 제출할 때
* reset : 리셋 버튼을 이용할 때
* cut : 폼 필드의 컨텐츠를 잘라냈을 때
* copy : 폼 필드의 컨텐츠를 복사했을 때
* paste : 폼 필드의 컨텐츠를 붙여넣을 때
* select : 텍스트를 선택했을 때

포커스 이벤트

* focus : 요소가 포커스를 얻었을 때 focusin
* blur : 포커스를 잃었을 때 focusout

드래그 앤 드롭 이벤트

* dragstart
* drag
* dragleave
* drop