## 1. PIVOT과 UNPIVOT

**1) pivot과 unpivot에 관해 자유로운 리소스를 이용해 학습하고 요약해주세요.**

```
pivot? 너 뭔데?
기존에 있던 테이블을 group by 걸기 보다 pivot 을 이용 (행으로 구성되어 있던 값을 열로 바꾼다)
첫 컬럼에 대한 group by를 포함하고 있다.

select * from (select ~~from where )
pivot (count(*) for dname in ('Accounting') as accounting)

unpivot(열을 행으로 바꾼다)
unpivot은 pivot과 정확히 반대임!
unpivot (기존 테이블에 입력된 데이터를 열로 표현할 값 for 행 값들 as '데이터 값')

```

예시:

[[SQLD 모든 것] 26. PIVOT, UNPIVOT절 | SQL 피봇팅 | 아이리포](https://www.youtube.com/watch?v=FINRIH6Bmq0)

**2) 다음 문제를 풀어주세요**

[Occupations | HackerRank](https://www.hackerrank.com/challenges/occupations/problem)

![스크린샷](./스크린샷/스크린샷%202024-12-03%20오후%209.53.07.png)

```
/*제공된 유투브 파일이 잘 실행되는지 적용해본 쿼리이다. 여기서 count로 된 값을 이름만 출력되게끔 전환해야한다. 
select * from 
(select name, occupation from OCCUPATIONS)
pivot ( count(*) for occupation in ('Doctor' as Doctor, 'Actor' as Actor,
       'Professor' as professor, 'Singer' as Singer)
    )*/;

도무지 이해할 수 없어서 블로그의 글을 해석하는 방식으로 문제를 풀이했다. 그럼에도 이런 문제 풀이가 많았으면 좋겠다
select  
    min(case when occupation = 'Doctor' then name end) 'Doctor',
    min(case when occupation = 'Professor' then name end) 'Professor',
    min(case when occupation = 'Singer' then name end) 'Singer',
    min(case when occupation = 'Actor' then name end) 'Actor'
from (
  select *, row_number() over (partition by occupation order by name) rn
  from occupations
) t
group by rn

-- case를 나누어 해당 직업일 경우 name을 반환한다. 그리고 해당 name을 기준으로 정렬해야하므로 min을 사용한다. 
그리고 이렇게 정렬된 값은 최솟값만을 도출하게 된다.
-- 따라서 그 이후의 과정은 occupation 별로 partition by 함수를 이용해 직업 별로 묶은 뒤 직업별 항목의 행 넘버를 지정해준다. 그리고 이때의 order by는 name 기준으로 배정되기에 새로운 테이블을 만들 수 있는 것이다.  
-- 그리고 마지막 행넘버를 기준으로 group by로 묶어준다면 첫 행에는 1번 값을 지닌 name을 출력, 그리고 2번째는 2번값을 지닌 name을 출력.... 이런식으로 진행된다.  

```
-어렵다면 아래 소스를 참고하셔도 좋습니다.

[[SQL] CASE WHEN으로 Pivot Table 만들기(HackerRank - Occupations 문제)](https://techblog-history-younghunjo1.tistory.com/159)

## 2. 성능 최적화 기법

**1) 아래 칼럼을 읽고 요약해주세요.**

```
정말 좋은 내용 감사합니다~ ㅎㅎ 새로운 내용이라서 신기하기도 했고 이런 튜닝 과정이 궁금했는데 찍먹 해본 느낌이라 좋았어요!

인덱싱? > db에서 원하는 정보를 찾기 위한 지름길을 만드는 것

## 1. 좌변연산을 하지 말것 
# 데이터 원본을 변형하여, 내가 찾고자 하는 범위와 비교하는 연산은 데이터베이스가 인덱스를 제대로 활용할 수 없게 만든다. 
ex) year(date) = 2021
then how? > 우변에서의 데이터 필터링! 
WHERE date >= '2021-01-01' AND date <= '2021-12-31'; 
> Date 컬럼을 있는그대로 사용한다.

2. or 대신 union을 사용하자

만약 중복이 없다는 게 확실하다면 UNION ALL을 사용해 중복 제거 단계를 건너뛰고 성능을 더 높일 수도 있다. 

3. 필요한 Row와 Column만 선택하여 성능 최적화하기

4. 분석 함수를 활용하여 쿼리 성능 높이기
ROW_NUMBER(), RANK(), DENSE_RANK(), LEAD(), LAG() 등의 함수를 사용하기
어떻게 도움이 될까?
>>  전통적인 집계 함수와 달리 사전에 데이터를 그룹화할 필요가 없다 / 중간 결과물의 저장과 재처리를 최소화할 수 있다

5. 와일드카드(%)는 끝에 작성하는 것이 더 좋다

6. 계산값을 미리 저장해두었다가, 나중에 조회할 것
값을 매번 계산하는 것이 아니라 관련된 테이블을 만들어두고 계산이 필요할 때마다 꺼내쓰는 느낌으로!
```


칼럼 내용에 기반해 문제를 출제했습니다. 
**2) 문제를 풀어주세요.**

[SQL 쿼리 성능 최적화를 위한 튜닝 팁 6가지 (Query Optimization)](https://community.heartcount.io/ko/query-optimization-tips/)

## 문제

여러분은 `customer_orders`라는 테이블을 관리하는 데이터베이스 관리자로 일하고 있습니다. 이 테이블에는 고객의 주문 정보가 저장되어 있으며, 각 고객이 주문한 제품과 수량, 가격 정보가 포함되어 있습니다. 또한, 고객들이 특정 제품을 재구매한 비율을 계산하려고 합니다.

### 테이블 구조:

1. **customers** 테이블
    - `customer_id` (고객 ID, PRIMARY KEY)
    - `name` (고객 이름)
2. **orders** 테이블
    - `order_id` (주문 ID, PRIMARY KEY)
    - `customer_id` (고객 ID, FOREIGN KEY)
    - `order_date` (주문 날짜)
3. **order_details** 테이블
    - `order_id` (주문 ID, FOREIGN KEY)
    - `product_id` (제품 ID)
    - `quantity` (수량)
    - `unit_price` (단가)

---

### 요구 사항:

1. **`avg_order_value`**: 고객별 평균 주문 금액을 계산하여 `customers` 테이블에 업데이트하세요.
    - `avg_order_value`는 각 고객이 한 번의 주문에서 지출한 평균 금액입니다.
2. **`total_spent`**: 고객별 총 지출 금액을 계산하여 `customers` 테이블에 업데이트하세요.
    - `total_spent`는 고객이 지금까지 지출한 총 금액입니다.
3. **`num_orders`**: 고객이 총 몇 번의 주문을 했는지 계산하여 `customers` 테이블에 업데이트하세요.
    - `num_orders`는 고객이 주문한 총 개수입니다.
4. **`repurchase_rate`**: 고객의 재구매 비율을 계산하여 `customers` 테이블에 업데이트하세요.
    - `repurchase_rate`는 각 고객이 2번 이상 주문한 제품 비율을 의미합니다. (즉, 재구매한 제품이 전체 구매 제품 중 몇 퍼센트를 차지하는지)

### 예시:

- 고객 A는 3번 주문을 했고, 그 중 2개의 제품을 재구매했습니다.
    - 평균 주문 금액: 100,000원
    - 총 지출 금액: 300,000원
    - 주문 횟수: 3번
    - 재구매 비율: 66.67%

---

### 정답

```sql
UPDATE customers c
set 
  avg_order_value = (select 
    avg(od.quantity * od.unit_price) from order_details od
      join orders o on od.order_id = o.order_id
        where c.customer_id = o.customer_id       
  ),
  total_spent = (select sum(od.quantity * od.unit_price) from od
     JOIN orders o ON od.order_id = o.order_id
        WHERE o.customer_id = c.customer_id
 --  이 부분이 헷갈렸다 조인을 세 번 걸어줘야하나...?하는 생각을 가졌다. 하지만 여기서도 join을 걸어버리면 쿼리의 맨 위에 작성된 customer 테이블을 다시 참조해버리는 꼴이 되어버려 where를 사용해 묶는 것이 바람직해보인다.  
 ),
  num_orders = (select count(distinct(o.order_id)) from orders o 
          WHERE o.customer_id = c.customer_id), 

repurchase_rate = (select  count(DISTINCT CASE WHEN od.product_id IN (
                SELECT product_id
                FROM order_details
                JOIN orders o ON order_details.order_id = o.order_id
                WHERE o.customer_id = c.customer_id
                group by od.product_id 
                having count(od.product_id) >1)
                then od.product_id End) *1.0 / count(distinct od.product_id)
                from od 
                join orders o on od.order_id = o.order_id
                where o.customer_id = c.customer_id)


```

---

### 추가 질문:

1. 정답 쿼리에서 `repurchase_rate`를 구할 때 사용한 `HAVING COUNT(order_details.product_id) > 1`의 의미는 무엇인가요?

```
주문의 수가 1번을 넘는 값을 대상으로만 repurchase_rate를 계산해야하기 때문에 해당 쿼리가 필요하다
```

2. 이 문제에서 사용될 수 있는 성능을 최적화하기 위한 방법은 무엇일까요?
```
뭔가 수량*가격을 통해 도출하는 것도 좋지만 해당 관련 값을 계산하여 테이블값을 만들어서 뽑는 경우 빨라질 것 같다.

그리고 case when을 쓰기보다 주문 수량의 테이블을 새로 만든 뒤 해당 열의 값이 1을 초과하는 행을 불러올 경우 최적화될 수 있지 않을까? 생각했다. 

```