# 문제 1
![screen](./스크린샷/3주차%20문제1.png)

```
select a.item_id, item_name from ITEM_INFO as a
inner join item_tree as b on
a.item_id = b.item_id
where parent_item_id is null
```

# 문제 2

![screen](./스크린샷/3주차%20문제2.png)

```
select ROUTE,concat(round(sum(D_BETWEEN_DIST),1),'km') as TOTAL_DISTANCE,
    concat(round(avg(D_BETWEEN_DIST),2),'km') as AVERAGE_DISTANCE
    from SUBWAY_DISTANCE
group by route
order by  sum(D_BETWEEN_DIST) desc
```

```
잘못 생각한 거 >> order by 할때 total distance를 기준으로 정렬했다. concat이 되어있으니 문자열로 인식하기에 따로 뺐어야했다
그리고 소숫점 1째자리까지 나타내고 싶으면 ,1)로 표현하자!
```

# 문제 3

![screen](./스크린샷/3주차%20문제%203.png)

```
select id, name, host_id from places
where host_id in
(
SELECT host_id from PLACES
group by host_id having count(host_id)>1
    )
order by id

```
```
언제나 정답은 행복하다!
having 뒤에 count() 써는 식으로 바로 연결해도 가능~
```