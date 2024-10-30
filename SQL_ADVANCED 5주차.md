문제 1

[스크린샷](./스크린샷/5주차%20문제%201.png)

SELECT INGREDIENT_TYPE, sum(TOTAL_ORDER) as TOTAL_ORDER
from FIRST_HALF as a
inner join ICECREAM_INFO as b on
a.FLAVOR = b.FLAVOR
group by INGREDIENT_TYPE
order by TOTAL_ORDER

>> 해메지 않고 바로 풀었다. 

문제 2