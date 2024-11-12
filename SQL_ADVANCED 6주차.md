# 문제 1

## 틀린 코드 이유 분석

SELECT *
FROM (
  SELECT FOOD_TYPE, REST_ID, REST_NAME, MAX(FAVORITES) AS FAVORITES
FROM REST_INFO
GROUP BY FOOD_TYPE
ORDER BY FOOD_TYPE DESC

1) 일단 괄호가 마무리 되지 않음 
2) 그리고 해당 조건으로 찾게 되면 favorites 중 max값을 가진 값을 출력해주지만, food_type과 rest_id 등은 max(favorites)와 대응하는 열을 출력해주지 않는다. 즉, 따로따로 다른 값을 출력하기에 옳지 않은 값이 도출된다.
>> 따라서 where 조건절로 묶어서 조회해야하는 것이다.
3) favorites로 이름을 변경하더라도 sql은 favorites열로 인식하지 못한다. 
>> 따라서 where 조건절로 묶어서 조회해야한다.


# 문제 2
## 
WITH RankedRest AS (
    SELECT 
        FOOD_TYPE, REST_ID, REST_NAME, FAVORITES,
        ROW_NUMBER() OVER (PARTITION BY FOOD_TYPE ORDER BY FAVORITES DESC, REST_ID) AS rnk
    FROM REST_INFO
)

/* with 구문을 이용해서 새로운 테이블을 제작한다. 
이때 원하는 열을 선택하여 자료를 출력하며, row_number를 이용해 각 열의 행을 출력하게끔 한다. 이때 음식점 종류에 따라 구분하고, row_num을 통해 순서를 부여하였으므로 각 파티션 별로 순위가 생성된다*/ 


SELECT 
    FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM RankedRest
WHERE rnk = 1
ORDER BY FOOD_TYPE DESC;

-- 여기서는 새롭게 만들어진 테이블을 이용해서 rnk = 1을 처리하여 구분이 가능해진다

장점
먼저 with 구문을 통해 테이블을 만들어 sql 구문을 구성한다면 자료를 따로 저장하지 않기에 데이터 처리속도가 빨라질 수 있다.
그리고 rnk = 1 이라는 값을 이용해서 처리하므로 조금 더 직관적인 sql 구문의 제작이 가능하다. 


# 문제 3
-[SUBQUERY] 조건에 맞는 사원 정보 조회하기

이것과 별개로 
rank, dense_rank, row_number()의 차이를 비교하자면
![스크린샷](./스크린샷/스크린샷%202024-11-12%20오후%2010.24.48.png)
먼저 rank는 랭킹 값이 sal에 따라 입력되며 동점자가 있는 경우 순위가 뒤로 밀려 2등이 2명 있는 경우 다음은 3이 아닌 4로 입력된다.
![스크린샷](./스크린샷/스크린샷%202024-11-12%20오후%2010.25.25.png)
dense_rank는 2등이 2명 있더라도 다음 순위는 3으로 입력된다.
![스크린샷](./스크린샷/스크린샷%202024-11-12%20오후%2010.27.20.png)
마지막으로 row_number는 말그대로 행의 값을 출력하는 함수로 그냥 행의 값으로 출력된다. 이때 값이 같은 경우는 emp_no 혹은 EMP_NAME의 값에 따라 정렬되는 순서로 행의 값이 책정되므로 주의하여야한다. 



![스크린샷](./스크린샷/스크린샷%202024-11-12%20오후%2010.16.10.png)

select 
    sum(score) as score, 
    a.EMP_NO, 
    EMP_NAME, 
    POSITION, EMAIL
from HR_EMPLOYEES a

inner join HR_GRADE b
    on a.EMP_NO = b.EMP_NO

group by a.EMP_NO 

order by score desc
limit 1

해당 문제의 답을 추가적으로 첨부해 보았다!