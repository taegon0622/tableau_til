# First Study Week

- 1강: [태블로설치](#1강-태블로설치)

- 2강: [데이터연결](#2강-데이터연결)

- 3강: [데이터연결과 데이터유형](#3강-데이터연결과-데이터유형)

- 4강: [데이터결합과 관계](#4강-데이터결합과-관계)

- 5강 : [데이터결합과 조인](#5-데이터결합과-조인)

- 6강: [데이터결합 혼합](#6강-데이터결합-혼합)

- 7강: [데이터결합과 유니온](#7강-데이터-결합과-유니온)

- 8강: [라이브 및 추출](#8강-라이브-및-추출)

- 9강: [데이터형식](#9강-데이터형식)

- 문제1 : [문제1](#문제-1)

- 문제2 : [문제2](#문제-2)

- 참고자료 : [참고자료](#참고-자료)


## Study Schedule

| 강의 범위     | 강의 이수 여부 | 링크                                                                                                        |
|--------------|---------|-----------------------------------------------------------------------------------------------------------|
| 1~9강        |  ✅      | [링크](https://youtu.be/3ovkUe-TP1w?si=CRjj99Qm300unSWt)       |
| 10~19강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=75)       |
| 20~29강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=65)       |
| 30~39강      | 🍽️      | [링크](https://www.youtube.com/watch?v=e6J0Ljd6h44&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=55)       |
| 40~49강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=45)       |
| 50~59강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=35)       |
| 60~69강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=25)       |
| 70~79강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=15)       |
| 80~89강      | 🍽️      | [링크](https://www.youtube.com/watch?v=AXkaUrJs-Ko&list=PL87tgIIryGsa5vdz6MsaOEF8PK-YqK3fz&index=5)        |


<!-- 여기까진 그대로 둬 주세요-->


## 1강. 태블로설치


<!-- 태블로 Desktop은 유료 혹은 사용자 인증이 되어야 하므로, 사용 경험이 없으시다면 우선 Tableau Public으로 학습하는 것을 권장드립니다. -->


## 2강. 태블로연결


> **🧞‍♀️ 데이터 해석기는 어떤 경우 사용하나요?**

```
데이터 해석기는 병합된 셀, 메모, 바닥글, 빈 셀을 확인하고 이를 무시하여 데이터 집합의 실제 필드와 값을 식별하는 것으로 태블로가 읽기 힘든 경우 사용한다. 
```


> **🧞‍♀️ 깃허브 assignment 폴더의 DArt-B Sample Store.xls 파일을 다운받고 시트 중 '주문' 시트를 불러와주세요.**


<!-- 캡쳐 파일을 첨부해주세요! 캡쳐하는 법은 깃허브 강의 영상에 있습니다 (폴더 생성 후 폴더 안에 이미지 넣기 + 불러오기) -->
![주문시트](./스크린샷/주문시트.png)


<!-- 문제와 문제 풀이가 모두 위 DArt-B Sample Store.xls 파일을 기반으로 제시되므로, 해당 엑셀파일을 사용하셔야 혼동이 없습니다. -->


## 3강. 데이터연결과 데이터 유형


> **🧞‍♀️ 라이브와 추출의 차이가 무엇인가요? 어떤 경우 사용하나요?**


```
라이브는 태블로가 데이터에 직접 연결 따라서 원본이 바뀌면 따라서 바뀐다. 속도가 느리다.
추출은 하이퍼로 형태로 저장. 오프라인에서도 가능하고 처리속도가 빠르며, 새로고침을 통해 최신화
```


## 4강. 데이터결합과 관계

<!-- 데이터 결합과 관계에 대해 알게 된 점을 자유로이 적어보세요.-->
데이터를 원하는 방식으로 분석하기 위해 결합을 해야함 >> 교집합이 된 값을 결합
이음줄에 !가 있는 경우 두 테이블 간 결합에 문제 / 필드는 고유값으로 / 연결필드를 수정, 새로운 필드를 추
가도 가능 / 맨처음 루트 테이블이 삭제 시 모두 삭제됨 / 두 개의 테이블이 독립적으로 유연하게 

> **🧞‍♀️ 어떤 경우에 관계를, 어떤 경우에 조인을 사용하나요?**

```
관계 > 조인보다 동적이고 유연 / 원본데이터를 독립적으로 활용가능
/데이터간의 유형이 동일해야함 즉, 각각의 테이블에서 같은 값을 가지고 있어야함.
조인에서 발생가능한 데이터 중복 및 필터링을 방지/ 테블로는 이걸 지향!
조인 > 5강

```


## 5강. 데이터결합과 조인

<!-- 데이터 결합과 조인에 대해 알게 된 점을 적고, 아래 질문에 답해보세요 :) -->
의도적인 필터링을 위해 조인을 함 / 여러 유형의 조인을 사용가능 > 이너 레프트 라이트 아우터

주문 중 '반품된' 주문만을 가지고 분석을 진행하려고 합니다.

> **🧞‍♀️ 해당 목적 달성을 위해서 Sample store 데이터셋의 어떤 시트를 조인(혹은 릴레이션)해야 할까요? 조인키는 무엇인지, (inner, outer, left, right) 조인 유형은 무엇일지 논의해주세요.**
주문시트와 반품정리 시트를 inner join으로 묶어서 사용한다

데이터를 조인한 데이터 원본 창의 캡쳐를 첨부해주세요.
몇 개의 주문이 반품되었다고 표시되나요?
3027개 

<!-- 캡쳐 이미지를 첨부해주세요 -->
![조인중복](./스크린샷/조인%20중복.png)

## 6강. 데이터결합 혼합

<!-- 데이터결합 및 혼합에 대해 알게 된 점을 적어주세요 --> 
테이블간의 상관관계를 파악하기 위해 데이터를 결합 /
혼합은 데이터를 실제로 결합하지는 않음. /
각 데이터를 독립적으로 결과를 집계 후 한 시트에서 데이터를 시각화하는 방법 /
실제 혼합 데이터 원본은 없고 혼합된 결과만 등장 /
새데이터 원본으로 테이블간 혼합 가능 /
결합방법으로는 혼합 방법을 추천하지 않음 / 


## 7강. 데이터 결합과 유니온

<!-- 유니온에 대해 알게 된 점을 적어주세요 -->
유니온은 테이블의 행을 다른 테이블에 추가해서 결합. / 데이터의 테이블 구조가 동일해야 / 
즉 밑에다 합치는 것 / 여러테이블을 유니온 하고 싶으면 유니온 편집에서 와일드 카드로 들어가서 수정 
ex> x가 들어가는 테이블을 모두 합치는 등 ...
> **🧞‍♀️ 유니온을 사용하기 위한 전제 조건은 무엇인가요?**
테이블의 구조가 동일해야함. 즉 각 테이블의 필드 수가 같고, 관련 필드의 필드 이름과 데이터 유형이 일치해야한다.


## 8강. 라이브와 추출

<!-- 라이브와 추출에 대해 알게 된 점을 적어주세요 -->

> **🧞‍♀️ 라이브와 추출 방법의 차이가 무엇인가요? 어떤 경우에 추출을 사용하면 좋을까요?**
데이터의 실시간 업데이트에 차이가 있다. 라이브는 실시간으로 업데이트
추출은 그렇지 않음. 추출을 매번 새로고침해야한다.
추출은 일정시간 마다 업데이트 되므로 데이터원본이 바뀌어도 시각화에 영향을 미치지 않는다.
대규모 데이터 셋 등 복잡한 시각화에서 속도가 빠르다. 즉, 일간 혹은 주간 추세 등을 파악하는 경우에 사용한다.




**참고자료 : 온프레미스 데이터란?**

기업이나 조직이 자체적으로 보유한 물리적 서버나 데이터 센터 내에서 직접 관리하는 데이터로, 조직 내의 하나 이상 서버에서 통제됩니다. 본 서버들은 기업의 데이터센터나 물리적 위치에 설치되어 있으며, 네트워크를 통해 해당 데이터에 접근하고 관리할 수 있습니다.


## 9강. 데이터형식

<!-- 데이터형식에 대해 알게 된 점을 적어주세요 -->
필터를 통해 원하는 조건에 해당하는 값만 가져올 수 있다. 엑셀의 정렬 느낌이다.
데이터 형식은 숫자 / 날짜 및 시간 / 날짜 / 문자열 / 부울.boolean임 / 
지구본은 지리적 역할

예를 들어 날짜값을 태블로에서 정수로 인식하는 경우가 있으니 이를 변경 할 수 있어야한다.
왼쪽은 메타데이터로 데이터에 대한 설명을 나타냄.

## 문제 1.

용웅이는 아래 사진과 같이 2024년 3월부터 7월까지의 지하철 승하차 이용객 데이터를 가지고 있습니다. 월별로 데이터셋이 나누어진 상태며, 용웅이는 해당 데이터셋 5개 모두를 한 번에 시각화하려 합니다. 필드 값(컬럼)의 이름, 데이터 유형, 개수는 모두 같습니다.

![image](https://github.com/yousrchive/BUSINESS-INTELLIGENCE-TABLEAU/blob/main/study/img/1st%20week/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202024-09-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.23.23.png?raw=true)



 이때, '조인, 관계, 혼합, 유니온' 중 본 목적에 적합한 결합 방법은 무엇인가요? 하나씩 드래그하지 않고, 와일드카드를 이용해 모든 데이터를 빠르게 결합해보세요.

<!-- 텍스트 및 이미지로 문제 풀이 과정을 기술해주세요 -->
모든 데이터 셋의 필드 값과 이름, 데이터 유형과 개수가 모두 같으므로, 유니온을 통해 결합하는 것이 좋다
3~7월까지의 값을 통합하여 하나의 테이블로 만드는 경우 보다 세부적인 분석이 가능하다. 


## 문제 2.

상원이는 태블로를 사용하여 회사의 매출 데이터를 시각화하려고 합니다. 태블로에서는 데이터를 연결하는 두 가지 방식인 **라이브 연결과 추출 연결**이 있습니다. 두 방식 중 어떤 것을 사용할지 고민 중입니다.

다음의 일상생활 사례를 바탕으로, 어떤 상황에서 라이브 연결이 적합하고, 어떤 상황에서 추출 연결이 더 적합한지 설명하세요.

1. 사례 1: 실시간 주식 시세 확인
주식 거래를 하고 있는 수금의왕 상원이는 주식 시세가 매 순간 변동하는 실시간 데이터를 필요로 합니다. 이 데이터를 기반으로 빠르게 결정을 내려야 합니다.


```
라이브!
```


2. 사례 2: 상원이는 저번 주 제주도로 여행을 갔었어요. 비행 중에 예산 계획을 세우려 하는데, 인터넷 연결이 불안정할 것 같아요. 여행 전 미리 예산 데이터를 다운로드해서 오프라인에서도 사용할 수 있으면 좋겠습니다.

```
추출!
```

## 참고 자료

데이터 분석을 하다보면 지역별로 경향을 알아보고자 할 때가 많습니다.

태블로에서는 시/도, 시군구명을 칼럼으로 가지고 있고, 그걸 지리적 위치로 바꿔주면 지도에서 위치를 인식하는데요.
하지만 읍면동(행정동) 단위까지 인식하지는 못합니다.

그럼 어떻게 읍면동 단위까지 세분화하여 표기할 수 있을까요?

이때 방금 배운 데이터 릴레이션 혹은 조인을 사용합니다.
맵 그래프는 지금 배울 부분은 아니지만, 데이터 병합에 관련된 부분이기에 필요하신 분들을 위해 아래 링크를 걸어두겠습니다.


![screen](https://github.com/yousrchive/BUSINESS-INTELLIGENCE-TABLEAU/blob/main/study/img/1st%20week/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202024-09-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.00.22.png?raw=true)

바로 읍면동의 경계를 가지고 있는 shp, geojson 등 공간파일을 원본데이터와 머지하는 것입니다.

링크: https://subinze.tistory.com/m/2
