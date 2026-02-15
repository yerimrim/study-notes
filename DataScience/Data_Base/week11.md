### 실습

```sql
USE resDB;

## 분석 1
SELECT COUNT(order_no) AS '전체주문건',
	   SUM(sales) AS '총매출',
       ROUND(AVG(sales),3) AS '평균매출',
       MAX(sales) AS '최고매출',
       MIN(sales) AS '최저매출'
FROM order_info;

## 분석 2
SELECT COUNT(O.order_no) AS '총판매량',
	   SUM(O.sales) AS '총매출',
       COUNT(IF(O.item_id = 'M0001', 1, NULL)) AS '전용상품_판매량',
	   SUM(IF(O.item_id = 'M0001', O.sales, 0)) AS '전용상품_매출' 
FROM order_info O
INNER JOIN reservation R
ON O.reserv_no = R.reserv_no
WHERE R.cancel = 'N';

## 분석 3
SELECT O.item_id AS '상품아이디',
	   I.product_name AS '상품이름',
       SUM(O.sales) AS '상품매출'
FROM order_info O
LEFT OUTER JOIN item I
ON O.item_id = I.item_id
GROUP BY O.item_id
ORDER BY sum(O.sales) DESC;

## 분석 4
SELECT LEFT(O.reserv_no,6) AS '매출월',
	     SUM(IF(I.product_name = 'SPECIAL_SET', O.sales, 0)) AS 'SPECIAL_SET',
	     SUM(IF(I.product_name = 'PASTA', O.sales, 0)) AS 'PASTA',
	     SUM(IF(I.product_name = 'PIZZA', O.sales, 0)) AS 'PIZZA',
       SUM(IF(I.product_name = 'SEA_FOOD', O.sales, 0)) AS 'SEA_FOOD',
       SUM(IF(I.product_name = 'STEAK', O.sales, 0)) AS 'STEAK',
	     SUM(IF(I.product_name = 'SALAD_BAR', O.sales, 0)) AS 'SALAD_BAR',
       SUM(IF(I.product_name = 'SALAD', O.sales, 0)) AS 'SALAD',
       SUM(IF(I.product_name = 'SANDWICH', O.sales, 0)) AS 'SANDWICH',
       SUM(IF(I.product_name = 'WINE', O.sales, 0)) AS 'WINE',
       SUM(IF(I.product_name = 'JUICE', O.sales, 0)) AS 'JUICE'
FROM order_info O
LEFT OUTER JOIN item I
ON O.item_id = I.item_id
GROUP BY LEFT(O.reserv_no, 6);

## 분석 5
SELECT LEFT(O.reserv_no, 6) AS '매출월',
	     SUM(O.sales) AS '총매출',
        SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품매출'
FROM order_info O
GROUP BY LEFT(O.reserv_no, 6);

## 분석 6
SELECT LEFT(O.reserv_no, 6) AS '매출월',
	     SUM(O.sales) - SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품외매출',
       SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품매출',
       ROUND(SUM(IF(O.item_id='M0001', O.sales, 0))/SUM(O.sales)*100,1) AS '매출기여율'
FROM order_info O
GROUP BY LEFT(O.reserv_no, 6);

## 분석 7-1
SELECT LEFT(O.reserv_no, 6) AS '매출월',
	     SUM(O. sales) AS '총매출',
	     SUM(O.sales) - SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품외매출',
       SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품매출',
       ROUND(SUM(IF(O.item_id='M0001', O.sales, 0))/SUM(O.sales)*100,1) AS '매출기여율',
       COUNT(R.reserv_no) AS '총예약건',
       COUNT(IF(R.cancel='N', 1, NULL)) AS '예약완료건',
       COUNT(IF(R.cancel='Y', 1, NULL)) AS '예약취소건'
FROM order_info O
LEFT OUTER JOIN reservation R
ON R.reserv_no = O.reserv_no
GROUP BY LEFT(O.reserv_no, 6);

## 분석 7-2
SELECT LEFT(R.reserv_no, 6) AS '매출월',
	     SUM(O. sales) AS '총매출',
	     SUM(O.sales) - SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품외매출',
       SUM(IF(O.item_id='M0001', sales, 0)) AS '전용상품매출',
       ROUND(SUM(IF(O.item_id='M0001', O.sales, 0))/SUM(O.sales)*100,1) AS '매출기여율',
       COUNT(R.reserv_no) AS '총예약건',
       COUNT(IF(R.cancel='N', 1, NULL)) AS '예약완료건',
       COUNT(IF(R.cancel='Y', 1, NULL)) AS '예약취소건'
FROM order_info O
RIGHT OUTER JOIN reservation R
ON R.reserv_no = O.reserv_no
GROUP BY LEFT(R.reserv_no, 6);

## 분석 8
SELECT LEFT(R.reserv_no, 6) AS '매출월',
	     SUM(O.sales) AS '총매출',
       SUM(O.sales) - SUM(IF(O.item_id='M0001', O.sales, 0)) AS '전용상품외매출',
	     SUM(IF(O.item_id='M0001', sales, 0)) AS '전용상품매출',
	     CONCAT(ROUND(SUM(IF(O.item_id='M0001',O.sales,0))/SUM(O.sales)*100,1), '%') AS '전용상품판매율',
       COUNT(R.reserv_no) AS '총예약건',
       COUNT(IF(R.cancel='N', 1, NULL)) AS '예약완료건',
       COUNT(IF(R.cancel='Y', 1, NULL)) AS '예약취소건',
       CONCAT(ROUND(COUNT(IF(R.cancel='Y', 1, NULL))/COUNT(R.reserv_no)*100, 1) ,'%') AS '예약취소율'
FROM order_info O
RIGHT OUTER JOIN reservation R
ON R.reserv_no = O.reserv_no
GROUP BY LEFT(R.reserv_no, 6);

## 분석 9
SELECT LEFT(reserv_no, 6) AS '날짜',
	     'SPECIAL_SET' AS '상품명',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=1, sales, 0)) AS '일요일',
	     SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=2, sales, 0)) AS '월요일',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=3, sales, 0)) AS '화요일',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=4, sales, 0)) AS '수요일',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=5, sales, 0)) AS '목요일',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=6, sales, 0)) AS '금요일',
       SUM(IF(DAYOFWEEK(STR_TO_DATE(reserv_no,'%Y%m%d'))=7, sales, 0)) AS '토요일'
FROM order_info
WHERE item_id = 'M0001'
GROUP BY LEFT(reserv_no, 6);

    
## 분석 10-1
SELECT * FROM(
	SELECT 
    LEFT(O.reserv_no,6) AS 날짜,
	  R.branch AS 방문지점,
	  SUM(IF(O.item_id='M0001',O.sales,0)) AS 전용상품매출,
	  RANK() OVER(PARTITION BY LEFT(O.reserv_no,6) ORDER BY SUM(IF(O.item_id='M0001',O.sales,0)) DESC) AS 지점순위
FROM order_info O
LEFT OUTER JOIN reservation R
ON O.reserv_no = R.reserv_no
GROUP BY LEFT(O.reserv_no,6), R.branch) AS 매출순위
WHERE 지점순위 <=3;

## 분석 10-2
SELECT * FROM(
SELECT
LEFT(O.reserv_no,6) AS 날짜,
R.branch AS 방문지점,
SUM(IF(O.item_id='M0001',O.sales,0)) AS 전용상품매출,
ROW_NUMBER() OVER(PARTITION BY LEFT(O.reserv_no,6) ORDER BY SUM(IF(O.item_id='M0001',O.sales,0)) DESC) AS 지점순위,
IF(R.branch IN ('강남','종로','영등포'), 'A', 'B') AS 지점등급
FROM order_info O
LEFT OUTER JOIN reservation R
ON O.reserv_no = R.reserv_no
GROUP BY LEFT(O.reserv_no,6), R.branch) AS 매출순위
WHERE 지점순위 =1;
```
