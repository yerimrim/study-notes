```sql
USE resDB;

## 분석 12
SELECT COUNT(customer_id) AS 고객수,
	     COUNT(IF(sex_code='M', 1, NULL)) AS 남자,
       COUNT(IF(sex_code='F', 1, NULL)) AS 여자,
	     ROUND(AVG(TIMESTAMPDIFF(MONTH, CAST(birth AS DATE), '2017-12-31') / 12), 1) AS 평균나이,
	     ROUND(AVG(TIMESTAMPDIFF(MONTH, CAST(first_reg_date AS DATE), '2017-12-31')),1) AS 평균거래기간
FROM customer;

## 분석 13
SELECT C.customer_id AS 고객아이디,
	     C.customer_name AS 고객이름,
       SUM(O.quantity) AS 전체상품주문건수,
       SUM(O.sales) AS 총매출,
       SUM(IF(O.item_id='M0001', O.quantity, 0)) AS 전용상품주문건수,
       SUM(IF(O.item_id='M0001', O.sales, 0)) AS 전용상품매출
FROM customer C
LEFT OUTER JOIN reservation R
ON C.customer_id = R.customer_id
LEFT OUTER JOIN order_info O
ON R.reserv_no = O.reserv_no
GROUP BY C.customer_id, C.customer_name
ORDER BY 전용상품매출 DESC;

## 분석 14
# 전체 고객의 거주지
SELECT A.address_detail AS 주소,
	     A.zip_code AS ZIP_CODE,
       COUNT(C.customer_id) AS 카운팅
FROM address A
LEFT OUTER JOIN customer C
ON A.zip_code = C.zip_code
GROUP BY A.address_detail, A.zip_code
ORDER BY 카운팅 DESC;

# 전용 상품을 구매한 고객의 거주지
SELECT A.address_detail AS 주소,
       A.zip_code AS ZIP_CODE,
       COUNT(IF(O.item_id='M0001', C.customer_id, NULL)) AS 카운팅
FROM address A
LEFT OUTER JOIN customer C
ON A.zip_code = C.zip_code
LEFT OUTER JOIN reservation R
ON C.customer_id = R.customer_id
LEFT OUTER JOIN order_info O
ON R.reserv_no = O.reserv_no
GROUP BY A.address_detail, A.zip_code
ORDER BY 카운팅 DESC;

# 전체 고객의 직업
SELECT IF(job IS NULL, '정보없음', job) AS 직업,
       COUNT(customer_id) AS 카운팅
FROM customer
GROUP BY 직업
ORDER BY 카운팅 DESC;

# 전용 상품을 구매한 고객의 직업
SELECT IF(C.job IS NULL, '정보없음', job) AS 직업,
       COUNT(C.customer_id) AS 카운팅
FROM customer C
LEFT OUTER JOIN reservation R
ON C.customer_id = R.customer_id
LEFT OUTER JOIN order_info O
ON R.reserv_no = O.reserv_no
WHERE O.item_id = 'M0001'
GROUP BY 직업
ORDER BY 카운팅 DESC;

## 분석 15
SELECT C.customer_id AS CUSTOMER_ID,
	     C.customer_name AS CUSTOMER_NAME,
       SUM(IF(O.item_id='M0001', sales, 0)) AS 전용상품매출,
       ROW_NUMBER() OVER(ORDER BY SUM(IF(O.item_id='M0001', sales, 0)) DESC) AS 순위
FROM customer C
LEFT OUTER JOIN reservation R
ON C.customer_id = R.customer_id
LEFT OUTER JOIN order_info O
ON R.reserv_no = O.reserv_no
GROUP BY CUSTOMER_ID, CUSTOMER_NAME
ORDER BY 전용상품매출 DESC
LIMIT 10;

# 거주지
SELECT A.address_detail AS 주소,
	     COUNT(*) AS 카운팅
FROM (SELECT C.customer_id
	  FROM customer C
      LEFT OUTER JOIN reservation R
      ON C.customer_id = R.customer_id
      LEFT OUTER JOIN order_info O
      ON R.reserv_no = O.reserv_no
      GROUP BY C.customer_id
      ORDER BY SUM(IF(O.item_id='M0001', sales, 0)) DESC
      LIMIT 10) AS K
INNER JOIN customer C
ON K.customer_id = C.customer_id
INNER JOIN address A
ON C.zip_code = A.zip_code
GROUP BY A.address_detail
ORDER BY 카운팅 DESC;
	
# 직업
SELECT IF(C.job IS NULL, '정보없음', C.job) AS 직업,
       COUNT(*) AS 카운팅
FROM (SELECT C.customer_id
	  FROM customer C
      LEFT OUTER JOIN reservation R
      ON C.customer_id = R.customer_id
      LEFT OUTER JOIN order_info O
      ON R.reserv_no = O.reserv_no
      GROUP BY C.customer_id
      ORDER BY SUM(IF(O.item_id='M0001',sales,0)) DESC
      LIMIT 10) AS P
INNER JOIN customer C
ON C.customer_id = P.customer_id
GROUP BY 직업
ORDER BY 카운팅 DESC;

## 분석 16
SELECT 고객아이디, 고객이름, 상품명, 상품매출, 선호도순위
FROM (
    SELECT 
        T.customer_id AS 고객아이디,
        C.customer_name AS 고객이름,
        I.product_name AS 상품명,
        SUM(O.sales) AS 상품매출,
        ROW_NUMBER() OVER (PARTITION BY T.customer_id ORDER BY SUM(O.sales) DESC
        ) AS 선호도순위
    FROM (
        SELECT C.customer_id
        FROM customer C
        LEFT JOIN reservation R ON C.customer_id = R.customer_id
        LEFT JOIN order_info O ON R.reserv_no = O.reserv_no
        GROUP BY C.customer_id
        ORDER BY SUM(IF(O.item_id = 'M0001', O.sales, 0)) DESC
        LIMIT 10
    ) AS T
    JOIN customer C ON T.customer_id = C.customer_id
    LEFT JOIN reservation R ON T.customer_id = R.customer_id
    LEFT JOIN order_info O ON R.reserv_no = O.reserv_no
    LEFT JOIN item I ON O.item_id = I.item_id
    WHERE O.item_id != 'M0001'
    GROUP BY T.customer_id, C.customer_name, I.product_name
) AS ranked
WHERE 선호도순위 = 1;
```
