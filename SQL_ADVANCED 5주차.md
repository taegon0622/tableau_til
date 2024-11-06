 # 문제 1

![스크린샷](./스크린샷/5주차%20문제%201.png)
 ``` 
 ## 문제풀이
SELECT INGREDIENT_TYPE, sum(TOTAL_ORDER) as TOTAL_ORDER
from FIRST_HALF as a
inner join ICECREAM_INFO as b on
a.FLAVOR = b.FLAVOR
group by INGREDIENT_TYPE
order by TOTAL_ORDER
 ``` 

 ``` 
해메지 않고 바로 풀었다. 
 ``` 

# 문제 2

![스크린샷](./스크린샷/5주차%20문제%202.png)
 ``` 
 ## 문제풀이
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
from REST_INFO
where (food_type,favorites) in (
    select food_type, max(favorites) from REST_INFO 
group by FOOD_TYPE )
    
order by FOOD_TYPE desc
 ``` 

 ``` 
where 로는 서브쿼리 중 하나의 항목만 지정가능하다.
where 안에 ( , )을 통해 조건을 지정해주자!
 ``` 


# 문제 3
![스크린샷](./스크린샷/5주차%20문제%203.png)

 ``` 
 ## 문제풀이
select sum(score) as score, a.EMP_NO, EMP_NAME, POSITION, EMAIL
from HR_EMPLOYEES a
inner join HR_GRADE b
on a.EMP_NO = b.EMP_NO
group by a.EMP_NO 
order by score desc
limit 1
 ``` 

 ``` 
가장 최댓값을 찾고 싶을 때는 order by desc limit 1을 쓰자
최솟값은 order by limit 1 이겠지!
 ``` 