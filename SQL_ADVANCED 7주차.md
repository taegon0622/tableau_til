**-[ISNULL] NULL처리하기 (SQL 고득점kit)**

[](https://school.programmers.co.kr/learn/courses/30/lessons/59410)

**동물의 생물 종, 이름, 성별 및 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성합니다.**

이때, 이름이 없는 동물의 이름은 ‘No name’으로 합니다.

**문제1. IFNULL()으로 해결**

![스크린샷](./스크린샷/7주차%20문제1.png)

```sql

SELECT ANIMAL_TYPE, IFNULL(NAME,"No name"), SEX_UPON_INTAKE  from ANIMAL_INS
order by ANIMAL_ID
-- ifnull은 a값이 null 인 경우 b의 값으로 치환하는 함수이다. 그리고 IFNULL은 select 문에서 작성할 수 있다. 
```

같은 문제를, CASE WHEN 문법을 사용하여 해결해주세요

**문제2. CASE WHEN으로 해결**

```sql
SELECT ANIMAL_TYPE, 
 case when name is null then "No name"
 Else  NAME
 end as name , 
 SEX_UPON_INTAKE  from ANIMAL_INS
order by ANIMAL_ID

-- case when a is x then " 원하는 값"
-- case when a is y then " 원하는 값"
-- end as a 

-- 이것도 가능하다 
-- case a when x then " 원하는 값"

```

**-중성화 여부 파악하기**

[](https://school.programmers.co.kr/learn/courses/30/lessons/59409#qna)

**문제 3. 문제를 풀어주세요 (힌트: IF, LIKE를 사용할 수 있습니다)**
![스크린샷](./스크린샷/7주차%20문제2.png)

```sql
SELECT ANIMAL_ID, NAME,if(SEX_UPON_INTAKE like '%Neutered%' or SEX_UPON_INTAKE like '%Spayed%', "O","X") as 중성화
from ANIMAL_INS
order by  ANIMAL_ID

-- if문은 if(조건문, 참이면 도출되는 값, 거짓이면 도출되는 값)
```

**문제 4. 아래는 QnA에 올라온 질문입니다. 왜 풀이가 틀렸는지 답해주세요.**

```
내가 처음에 저렇게 풀었는데 도출된 값과 비교해보니 처음 항목인 neutered만을 인식해서 n값만 도출한다. spayed 값은 도출하지 않는데 or의 특성때문이다.
조건을 완전하게 조합해야한다. 이를 위해 위의 식처럼 열 이름이 like ???를 추가해줘야 한다. 
```



