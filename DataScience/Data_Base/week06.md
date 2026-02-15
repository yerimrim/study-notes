<aside>
💡

### 이론

- **조작어, DML** (Data Manipulation Language): 데이터를 검색, 삽입, 수정, 삭제
    - SELECT, INSERT, UPDATE, DELETE
- **정의어, DDL** (Data Definition Language): 개체를 생성, 삭제, 변경
    - CREATE, ALTER, DROP, TRUNCATE
- **제어어, DCL** (Data Control Language): 권한을 부여, 삭제
    - GRANT, REVOKE, DENY
</aside>

<aside>
💡

### 실습

```sql
## INSERT ##
# 테이블 생성
CREATE TABLE testTBL1 (id INT, userName CHAR(3), age INT);
# 데이터 삽입
INSERT INTO testTBL1 VALUES (1, '뽀로로', 16);
# 일부 열만 입력
INSERT INTO testTBL1 (id, userName) VALUES (2,'크롱');
# 열 순서 바꿔서 입력
INSERT INTO testTBL1 (userName, age, id) VALUES ('루피', 14, 3);
# 여러 데이터 한 번에 입력
INSERT INTO testTBL3 VALUES (NULL, '토이', 17), (NULL, '스토리', 18), (NULL, '무비', 19);

# 기존 테이블에서 일부 데이터만 복사해오기
CREATE TABLE testTBL4(id INT, Fname VARCHAR(50), Lname VARCHAR(50));
INSERT INTO testTBL4 
SELECT emp_no, first_name, last_name FROM employees.employees;

# 기존 테이블에서 일부 데이터만 복사해오기 (테이블 정의 생략)
CREATE TABLE testTBL5
(SELECT emp_no, first_name, last_name FROM employees.employees);

# 기존 테이블에서 일부 데이터 복사하고, colname 변경 (테이블 정의 생략)
CREATE TABLE testTBL6
(SELECT emp_no AS id, first_name AS Fname, last_name AS Lname FROM employees.employees);

## AUTO_INCREMENT ##
# AUTO_INCREMENT는 'PRIMARY KEY' 또는 'UNIQUE + NOT NULL'에서만 설정 가능
# 데이터 형식이 숫자인 열에만 AUTO_INCREMENT 설정 가능
# AUTO_INCREMENT로 설정된 열은 NULL값으로 입력시 자동으로 값이 입력됨
CREATE TABLE testTBL2
(id INT AUTO_INCREMENT PRIMARY KEY,
 userName CHAR(3),
 age INT);
INSERT INTO testTBL2 VALUES (NULL, '에디', 15); # NULL이 1로 입력됨
INSERT INTO testTBL2 VALUES (NULL, '포비', 12); # NULL이 2로 입력됨
INSERT INTO testTBL2 VALUES (NULL, '통통이', 11); # NULL이 3으로 입력됨

## ALTER TABLE ##
ALTER TABLE testTBL2 AUTO_INCREMENT = 100; # 이후부터 입력되는 값의 AUTO_INCREMENT는 100부터 시작함
INSERT INTO testTBL2 VALUES (NULL, '패티', 13); # NULL이 100으로 입력됨

## SET @@auto_increment_increment = n; ##
CREATE TABLE testTBL3
(id INT AUTO_INCREMENT PRIMARY KEY,
 userName CHAR(3),
 age INT);

ALTER TABLE testTBL3 AUTO_INCREMENT = 1000; # AUTO_INCREMENT가 1000부터 시작
SET @@AUTO_INCREMENT_INCREMENT = 3; # AUTO_INCREMENT가 3단위로 증가
INSERT INTO testTBL3 VALUES (NULL, '우디', 20); # id=1000
INSERT INTO testTBL3 VALUES (NULL, '버즈', 18); # id=1003
INSERT INTO testTBL3 VALUES (NULL, '제시', 19); # id=1006
```

</aside>

<aside>
💡

### 실습

```sql
## UPDATE ## (UPDATE - SET - WHERE -)
# Fname이 'Kyoichi'인 데이터만 Lname을 '없음'으로 업데이트
UPDATE testTBL4
SET Lname = '없음'
WHERE Fname = 'Kyoichi';

# 전체 데이터의 price를 1.5배
UPDATE buyTBL
SET price = prcie * 1.5;
#####################################################
## DELETE ## (DELETE FROM - WHERE -)
# testTBL4에서 Fname이 'Aamer'인 데이터 모두 삭제
DELETE FROM testTBL4 WHERE Fname = 'Aamer';
# testTBL4에서 Fname이 'Aamer'인 데이터 중 상위 5개만 삭제
DELETE FROM testTBL4 WHERE Fname = 'Aamer' LIMIT 5;

## DELETE, DROP, TRUNCATE ##
DELETE FROM bigTBL1;
DROP TABLE bigTBL2;
TRUNCATE TABLE bigTBL3;
# 속도 DROP, TRUNCATE, DELETE 순으로 빠름
# 테이블 자체 삭제: DROP
# 테이블의 구조 유지: TRUNCATE, DELETE

#####################################################
# 데이터 가져와서 새로운 테이블 생성 (괄호 생략 가능)
CREATE TABLE memberTBL (SELECT userID, userName, addr FROM userTBL LIMIT 3);
# PK 추가 (ADD CONSTRAINT: 제약조건 추가)
ALTER TABLE memberTBL
ADD CONSTRAINT pk_memberTBL PRIMARY KEY (userID);

# error, 데이터 입력 안 됨 (because of 첫 문장 userID 중복, userID는 PRIMARY KEY이기 때문)
INSERT INTO memberTBL VALUES ('KHD', '강후덜', '미국');
INSERT INTO memberTBL VALUES ('LSM', '이상민', '서울');
INSERT INTO memberTBL VALUES ('KSJ', '김성주', '경기');

# PK가 중복된 첫 문장 제외하고, 2,3번 데이터는 입력됨
INSERT IGNORE INTO memberTBL VALUES ('KHD', '강후덜', '미국');
INSERT IGNORE INTO memberTBL VALUES ('LSM', '이상민', '서울');
INSERT IGNORE INTO memberTBL VALUES ('KSJ', '김성주', '경기');

# PRIMARY KEY가 중복이어도 데이터 입력됨, 기존 데이터가 바뀌는 거임 (무결성 유지)
INSERT INTO memberTBL VALUES('KHD','강후덜','미국')
ON DUPLICATE KEY UPDATE userName='강후덜', addr='미국';
#####################################################
## 윈도우 함수는 항상 OVER() 필요 ##
## 비집계함수 ##
## 순위 함수 ## RANK(), DENSE_RANK(), ROW_NUMBER(), NTILE()

## ROW_NUMBER() ##
# 키 큰 순서로 정렬
SELECT ROW_NUMBER() OVER(ORDER BY height DESC)
'키큰순위', userName, addr, height 
FROM userTBL;

# 키 큰 순서로 정렬 (키가 같은 경우, 이름 순으로 정렬)
SELECT ROW_NUMBER() OVER(ORDER BY height DESC, userName ASC)
'키큰순위', userName, addr, height 
FROM userTBL;

# 지역별로 나눠서 키 큰 순서로 정렬 (키가 같은 경우 이름 순으로 정렬)
# column: addr, '지역별키큰순위', userName, height
SELECT addr, ROW_NUMBER() OVER(PARTITION BY addr ORDER BY height DESC, userName ASC)
'지역별키큰순위', userName, height 
FROM userTBL;

## DENSE_RANK() ##
# 키 큰 순서로 정렬 (키가 같은 경우 동일한 순위로 입력, 순위 간격 x)
SELECT DENSE_RANK() OVER(ORDER BY height DESC)
'키큰순위', userName, addr, height
FROM userTBL;

## RANK() ##
# 키 큰 순서로 정렬 (키가 같은 경우 동일한 순위로 입력, 순위 간격 o)
SELECT RANK() OVER(ORDER BY height DESC)
'키큰순위', userName, addr, height
FROM userTBL;

## NTILE(n) ## n개의 그룹 분리
# 키 큰 순서로 정렬 후, 2개의 그룹으로 나눔
SELECT NTILE(2) OVER(ORDER BY height DESC)
'반번호', userName, addr, height
FROM userTBL;
#####################################################
## LEAD(col, n1, n2) ## n1만큼 뒤의 행 참조, 참조할 데이터가 없다면 n2를 참조
# 키 큰 순서로 정렬 후, 다음 사람과의 키 차이 column 추가
SELECT userName, addr, height AS '키',
height - (LEAD(height, 1, 0) OVER(ORDER BY height DESC)) AS '다음 사람과의 키 차이'
FROM userTBL;

## FIRST_VALUE(col) ##
# 지역별로 나눠서 키 큰 순서로 정렬, 지역별 최대키와의 차이 column 추가
SELECT addr, userName, height AS '키',
height - (FIRST_VALUE(height) OVER(PARTITION BY addr ORDER BY height DESC)) AS '지역별 최대키와 차이'
FROM userTBL;
# + 순위
SELECT ROW_NUMBER() OVER(PARTITION BY addr ORDER BY height DESC) AS '지역별 키 순위',
addr, userName, height,
height - FIRST_VALUE(height) OVER(PARTITION BY addr ORDER BY height DESC) AS '지역별 최대 키와 차이'
FROM userTBL;

## CUME_DIST() ## 해당 그룹에 대한 상대적인 누적분포도 값 반환
# 지역별로 나눠서 키가 큰 순으로 정렬한 후, 각 지역에 대한 '누적인원 백분율%' column 추가
SELECT addr, userName, height AS '키',
(CUME_DIST() OVER(PARTITION BY addr ORDER BY height DESC)) * 100 AS '누적인원 백분율%'
FROM userTBL;
#####################################################
## pivot 테이블 ##
# 테이블 만들기
USE cookDB;
CREATE TABLE pivotTest
(uName CHAR(3), season CHAR(2), amount INT);

INSERT INTO pivotTest VALUES ('유재석', '겨울', 10);
INSERT INTO pivotTest VALUES ('강호동', '여름', 15);
INSERT INTO pivotTest VALUES ('유재석', '가을', 25);
INSERT INTO pivotTest VALUES ('유재석', '봄', 3);
INSERT INTO pivotTest VALUES ('유재석', '봄', 37);
INSERT INTO pivotTest VALUES ('강호동', '겨울', 40);
INSERT INTO pivotTest VALUES ('유재석', '여름', 14);
INSERT INTO pivotTest VALUES ('유재석', '겨울', 22);
INSERT INTO pivotTest VALUES ('강호동', '여름', 64);

# 피벗 테이블 만들기 (봄일 때만 amount를 SUM하고, 그것을 '봄 합계'라 저장)
# 그룹별로 SUM 사용시 GROUP BY 필수!!!
SELECT uName,
			 SUM(CASE WHEN season='봄' THEN amount END) AS '봄 합계'
			 SUM(CASE WHEN season='여름' THEN amount END) AS '여름 합계'
			 SUM(CASE WHEN season='가을' THEN amount END) AS '가을 합계'
			 SUM(CASE WHEN season='겨울' THEN amount END) AS '겨울 합계'
FROM pivotTest
GROUP BY uName;
#####################################################
SELECT userID AS '사용자', SUM(price * amount) AS '총구매액'
FROM buyTBL
GROUP BY userID;

## CTE ##
# 회원별 총구매액 추출 (CTE 내부 컬럼 모두 출력)
WITH abc(userID, total)
AS (SELECT userID, SUM(price * amount) FROM buyTBL GROUP BY userID)
SELECT * FROM abc ORDER BY total AS '회원별 총구매액' DESC;

# 지역별로 나눠서 최고키 추출 (CTE 내부 컬럼 모두 출력)
WITH cte_userTBL(addr, maxHeight)
AS (SELECT addr, MAX(height) FROM userTBL GROUP BY addr)
SELECT * FROM cte_userTBL ORDER BY maxHeight DESC;

# 지역별로 나눠서 최고키 추출, 최고키의 평균을 실수로 출력 (평균만 출력)
WITH cte_userTBL(addr, maxHeight)
AS (SELECT addr, MAX(height) FROM userTBL GROUP BY addr)
SELECT AVG(maxHeight * 1.0) AS '각 지역별 최고키의 평균' FROM cte_userTBL;

# mobile1이 같은 것들끼리 나눠서 생일이 가장 빠른 것 추출, (CTE 내부 컬럼 모두 출력)
WITH cte_userTBL (mobile1, old_user)
AS (SELECT mobile1, min(birthYear) FROM userTBL GROUP BY mobile1)
SELECT * FROM cte_userTBL ORDER BY old_user;
```

</aside>
