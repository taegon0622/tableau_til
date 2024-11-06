# 문제 1

## 틀린 코드 이유 분석

SELECT *
FROM (SELECT FOOD_TYPE, REST_ID, REST_NAME, MAX(FAVORITES) AS FAVORITES
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