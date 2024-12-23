---
layout: post
title: 프론트엔드 면접 질문
date: 2024-08-08 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [IT,]
tags: IT
published: true
sitemap: true
---

# 프론트엔드 면접 질문

첫번째 면접에서 대차게 망하고 다시 공부하고 혼자보기위해 쓰는 글이다. 처음이다보니 당연히 기대도 안했지만 긴장한것과 별개로 공부를 안한게 스스로 느껴졌다. 이번 면접은 코딩테스트, 기술면접, 인성면접, 추가적인 기술면접 및 질문들을 받으며, 총 1시간 20분정도 면접을 보고 마지막엔 면접비를 주는데 별로 좋은 기분은 아니었다. 거리가 멀다보니 갈 생각도 없었고 면접연습을 하자는 느낌으로 간거였는데 왜이렇게 긴장하는지 잘 모르겠다. 본론으로 들어가서 받았던 질문들을 적는다.

## 코딩테스트

문제
````
The parameter in the array can only be random integers between -100000000 and 100000000.

What is the smallest positive integer that is not in parameter of an random array a?
random array a = [-6000, 2372, 2, -3, 7, -2, 10000, 1, 100, -12345, -1, 1000000]
````

번역
````
배열의 매개변수는 -100000000에서 100000000 사이의 임의의 정수만 가능합니다.

랜덤 배열 a에 존재하지 않는 가장 작은 양의 정수는 무엇입니까?
랜덤 배열 a = [-6000, 2372, 2, -3, 7, -2, 10000, 1, 100, -12345, -1, 1000000]
````

풀이
````
function findSmallestMissingPositive(arr) {
    // 양의 정수만 모으기
    const positives = arr.filter(num => num > 0);
    
    // 중복 제거 및 정렬
    const uniquePositives = [...new Set(positives)].sort((a, b) => a - b);
    
    // 1부터 시작하여 누락된 가장 작은 양의 정수 찾기
    let smallestMissing = 1;
    for (let num of uniquePositives) {
        if (num === smallestMissing) {
            smallestMissing++;
        } else if (num > smallestMissing) {
            break;
        }
    }
    
    return smallestMissing;
}

const a = [-6000, 2372, 2, -3, 7, -2, 10000, 1, 100, -12345, -1, 1000000];
console.log(findSmallestMissingPositive(a)); // Output: 3
````

1. 배열에서 양의 정수만 필터링합니다.
result : a = [2372, 2, 7, 10000, 1, 100, 1000000]
2. 양의 정수 배열에서 중복을 제거하고 오름차순으로 정렬합니다.
result : a = [1, 2, 7, 100, 2372, 10000, 1000000]
3. 1부터 시작하여 정렬된 양의 정수 목록을 순회하며 누락된 가장 작은 양의 정수를 찾습니다.
| num |smallestMissing | result |
| ---- |---- |  ------ |
|1 |1 |2 |
|2 |2 |3 |
|7 |3 |3 |

따라서, 배열에 존재하지 않는 가장 작은 양의 정수는 3입니다.

## 기술질문

1. 뷰 라이프사이클을 설명해주세요
2. var,let,const 차이점 설명해주세요
3. restful API 설명해주세요
4. 상태관리 툴 왜 쓰는지 설명해주세요
5. vercel은 어쩌다가 배포하게됬나요
6. 배포할때 어려웠던 점이 있나요
7. 이벤트루프에 대해 설명해주세요


## 인성질문

1. 팀프로젝트 진행중에 어떤역할을 했나요
2. 피드백을 받아본 경험이 있나요
3. 작업을 할때 어떤기준으로 우선순위를 정하나요?
4. 새로운 기술을 배우실때 어떤식으로 접근하고 가장 최근에 사용해본 기술은?
5. 어떤 개발자로 성장하고 싶은지, 어떤 노력을 할건지?

## 추가질문

1. 1byte가 몇 비트?
2. 자료형 큐,스택 설명
3. http method에서 patch가 뭐냐,put 차이점은?
4. http status
5. sql injection
6. xss
7. cors
8. csrf

대학나오고 왜 이쪽으로 안갔었냐
다른거 뭐해보고 싶었냐
어린친구들 이기려면 어떻게 해야될거같냐
별도 공부 몇시간할거냐


# 두번째 화상면접
살면서 미쳐본적이 있느냐
프로젝트를 진행하며 힘든경험을 해봤거나 그걸 극복한 경험
react의 상태변화
동기 비동기


# 세번째 면접
## 코딩테스트
spl join문
js로 html 뿌려주기
js로 php post방식으로 데이터 보내기 
