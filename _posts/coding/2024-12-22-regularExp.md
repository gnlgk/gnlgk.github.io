---
layout: post
title: javaScript
date: 2024-12-22 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 정규표현식

정규식.test(비교문자열) - 찾는 값이 있으면 true, 없으면 false, 첫번째값만 찾아서 확인

````html
<input type="text" pattern="정규식">   
<script>
const reExp = /love/ig; // g(global)를 붙이면 첫번째 값뿐만이 아니라 내용 끝까지 검색
                        // i(ignore case) 대소문자 상관없이 검색 lOve loVe lovE 등도 가능
const myS = "I Love zard.Zard is my love.";
document.write(reExp.test(myS));
</script>
````

````javaScript
g(global) - 전부 검색
i(ignore case) - 대소문자 구별없이 검색
m(Multi Line) - 문자열의 행이 바뀌더라도 계속 검색
. - 문자한글자 아무거나(숫자 포함) 한 글자
\. - .(마침표)로 사용
\\ - \(역슬래시) 사용

[0-9] - 0~9 글자 한 글자
[ns] - n또는s 글자 한 글자
[a-z0-9A-Z] - 중에 글자 한 글자

[A-z] - ASCII코드에서 기호까지 포함되므로 사용금지
^ - ^뒤의 종류만 제외하고 아무거나 허용

^ => 시작
$ => 끝
[^~~~] 빼고

/myArray\[0\]/ => myArray[0]

[\b] - 백스페이스
\f - 페이지 넘김
\n - 줄바꿈
\r - 캐리지 리턴
\t - 탭
\v - 수직 탭

\r\n\r\n - 한칸 띄기(enter 두번)
\r\n\t - 
````

## 고전적 자료교환 방식
CSV(Comma Seperated Value) - 어떤 정보의 분리를 ,로 나눈 것
{
    name: "zard",
    tel: "010-5678-1234"
}
zard , 010-5678-1234

줄바꿈
UNIX LF 
Windows CR+LF

윈도우에서 작업하려면 Docker 같은걸로 테스트한 후 unix에 올려야됨
(프론트 작업용 모니터 비싼거 쓰래 100~200) 디피니트 울트라샤프라? 울트라파이? 시리즈들 무조건 4k이상
노트북 - 삼성lg제일 비싼거, 씽크패드 400, 맥200

````javaScript
\d - 숫자 하나( == [0-9] )
\D - 숫자빼고 아무거나 한 글자( == [^0-9] )

\w - 대소문자와 밑줄을 포함하는 모든 영숫자( == [a-zA-Z0-9_]) (_포함)
\W - 영숫자나 밑줄이 아닌 모든 문자( == [^a-zA-Z0-9_]) (_포함)

\s - 모든 공백 문자( == [\f\n\r\t\v] ) (\b는 미포함)
\S - 공백 문자가 아닌 모든 문자( == [^\f\n\r\t\v] ) (\b는 미포함)

포직스 문법 - 표준안이 늦게나와서 안씀
````

````javaScript
const officeNum = [
	"11213",
    "A1C2E3",
    "48075",
    "AAH1H3H2BB"
]
const regPattern = /\w\d\w\d\w\d/;
officeNum.forEach((officeItem)=>{
	if( regPattern.test(officeItem) ) {
    	document.write(officeItem + "<br>");
    }
})
````