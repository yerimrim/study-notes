### 실습

```sql
SELECT 열이름
FROM 테이블이름
WHERE 조건
#####################################################
USE 데이터베이스이름; # 데이터베이스 불러오기
SELECT * FROM 테이블이름; # 테이블 내의 모든 데이터 불러오기
SELECT * FROM 데이터베이스이름.테이블이름; # 이미 해당 데이터베이스 안에 있는 경우 생략 가능

SELECT col1, col2 FROM 테이블이름; # 테이블 내의 특정 열만 불러오기
SELECT col2, col1 FROM 테이블이름; # 불러온 순서대로 열이 나타남.
SELECT col1, col2 FROM 테이블이름 LIMIT 10; # 10개까지만 출력

## SHOW DATABASES, SHOW TABLES, DESCRIBE, DESC ## 
SHOW DATABASES; # 모든 데이터베이스 확인
SHOW TABLES; # 현재 데이터베이스의 테이블 확인
DESCRIBE 테이블이름; # 테이블의 열이름, 타입 등 확인 #
DESC 테이블이름; # 테이블의 열이름, 타입 등 확인 #

# 별칭 설정 (공백 있을 시, ''작은따옴표 사용) (테이블의 열 이름 자체가 바뀌는 건 아님)
SELECT memberName AS 이름, memberID 아이디, memberAddress '회원 주소' 
FROM shopdb.memberTBL;

# 데이터베이스 및 테이블 생성
CREATE DATABASE 데이터베이스이름;
CREATE TABLE 테이블이름;

# 데이터베이스 및 테이블 삭제
DROP DATABASE 데이터베이스이름;
DROP TABLE 테이블이름;

# 테이블 생성 구체화
CREATE TABLE userTBL
(userID CHAR(8) NOT NULL PRIMARY KEY,
	userName VARCHAR(10) NOT NULL,
    birthYear INT NOT NULL,
    addr CHAR(2) NOT NULL,
    mobile1 CHAR(8),
    mobile2 CHAR(8),
    height SMALLINT,
    mDate DATE);

CREATE TABLE buyTBL
(num INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
 userID CHAR(8) NOT NULL,
 prodName CHAR(6) NOT NULL,
 groupName CHAR(4),
 price INT NOT NULL,
 amount SMALLINT NOT NULL,
 FOREIGN KEY (userID) REFERENCES userTBL (userID));

# 테이블 내에 데이터 입력 (INT형 외에 '' 작은 따옴표 필수!!)
INSERT INTO userTBL VALUES ('YJS', '유재석', 1972, '서울', '010', '11111111', 178, '2008-8-8');

#####################################################
SELECT 열이름 FROM 테이블이름 WHERE 조건식;
SELECT * FROM userTBL WHERE userName = '강호동';

## AND, OR, NOT, BETWEEN ##
SELECT userID, userName FROM userTBL WHERE birthYear>=1970 AND height>=182;
SELECT userID, userName FROM userTBL WHERE birthYear>=1970 OR height>=182;
SELECT userID, userName FROM userTBL WHERE NOT userName=강호동;
SELECT userID, userName FROM userTBL WHERE birthYear!=1970;
SELECT userName, height FROM userTBL WHERE height BETWEEN 180 AND 182;

## IN (이산형 value 조회시)
SELECT userName, addr FROM userTBL WHERE addr IN('경남', '충남', '경북');

## LIKE (% => 아무때나 사용 가능, _=> 뒤에 정확히 1개의 문자가 올 때만, __ => 뒤에 정확히 2개의 문자가 올 때)
SELECT userName, height FROM userTBL WHERE userName LIKE '김%';
SELECT userName, height FROM userTBL WHERE userName LIKE '_경규';
SELECT * FROM userTBL WHERE mDate LIKE '2007%';
#####################################################
## 서브쿼리 ##
SELECT userName, height FROM userTBL 
WHERE height > (SELECT height FROM userTBL WHERE userName='김용만');

## ALL, ANY ##
# ALL 경기에 사는 사람들 모두보다 키가 크거나 같으면 출력 (경기에 사는 사람 중 가장 키가 큰 사람보다 키가 큰 사람만 출력)
SELECT userName, height FROM userTBL 
WHERE height >= ALL (SELECT height FROM userTBL WHERE addr = '경기');
# ALL 서울에 사는 사람 중 박수홍을 제외하고 모두보다 키가 크면 출력 (서울에 사는 사람 중 박수홍 제외하고 가장 키가 큰 사람보다 키가 큰 사람만 출력)
SELECT height FROM userTBL 
WHERE height > ALL (SELECT height FROM userTBL WHERE addr = '서울' AND NOT userName = '박수홍');

# ANY 경기에 사는 사람 중 아무나보다 크거나 같으면 출력
SELECT userName, height FROM userTBL 
WHERE height >= ANY (SELECT height FROM userTBL WHERE addr = '경기');
# ANY 경기에 사는 사람 중 아무나와 키가 같으면 출력
SELECT userName, height FROM userTBL 
WHERE heigth = ANY (SELECT height FROM userTBL WHERE addr = '경기');
# =ANY(서브쿼리) 는 IN(서브쿼리) 와 같음
SELECT userName, height FROM userTBL 
WHERE height IN (SELECT height FROM userTBL WHERE addr = '경기');
# 서울에 사는 사람과 키가 같은 사람 출력 (단, 서울에 사는 사람 제외)
SELECT height FROM userTBL 
WHERE height = ANY (SELECT height FROM userTBL WHERE addr = '서울') 
AND NOT addr = '서울' ;

#####################################################
## ORDER BY (정렬) ##
# mDate를 기준으로 오름차순 정렬
SELECT userName, mDate FROM userTBL ORDER BY mDate;
# mDate 기준으로 내림차순 정렬
SELECT userName, mDate FROM userTBL ORDER BY mDate DESC;
# height 기준으로 내림차순 정렬 후, userName으로 오름차순 정렬 (ASC 생략 가능)
SELECT userName, height FROM userTBL ORDER BY height DESC, userName ASC;

## DISTINCT ##
# addr 출력
SELECT addr FROM userTBL;
# addr 기준으로 정렬하여 출력
SELECT addr FROM userTBL ORDER BY addr;
# 중복 없이 출력
SELECT DISTINCT addr FROM userTBL;
# addr 기준으로 정렬하여 중복 없이 출력
SELECT DISTINCT addr FROM userTBL ORDER BY addr;

## ORSER BY + LIMIT, LIMIT n1,n2 ##
# 상위 5개만 출력
SELECT emp_no, hire_date FROM employees ORDER BY hire_date LIMIT 5;
# 하위 5개만 출력
SELECT emp_no, hire_date FROM employees ORDER BY hire_date DESC LIMIT 5;
# LIMIT 시작 지점, 개수
SELECT first_name, hire_date FROM employees ORDER BY hire_date, first_name LIMIT 5;
SELECT first_name, hire_date FROM employees ORDER BY hire_date, first_name LIMIT 0,5;
SELECT first_name, hire_date FROM employees ORDER BY hire_date, first_name LIMIT 1,5;

## CREATE TABLE로 테이블 복사 ## (단, 기본키, 외래키 등 제약조건은 복사되지 않음!)
# buyTBL 전체를 buyTBL2에 그대로 복사
CREATE TABLE buyTBL2(SELECT * FROM buyTBL);
# buyTBL의 일부 열만 buyTBL3에 복사
CREATE TABLE buyTBL3(SELECT userID, prodName FROM buyTBL);
#####################################################
## GROUP BY ##
## SUM ##
# userID별 총 구매 개수
SELECT userID, SUM(amount) FROM buyTBL GROUP BY userID;
# 별칭 설정
SELECT userID AS '사용자 아이디', SUM(amount) AS '총 구매 개수' FROM buyTBL GROUP BY userID;
SELECT userID AS '사용자 아이디', SUM(price * amount) AS 총구매액 FROM buyTBL GROUP BY userID;

## AVG() ##
SELECT AVG(amount) AS '평균 구매 개수' FROM buyTBL;
SELECT userID, AVG(amount) AS '회원별 평균 구매 개수' FROM buyTBL GROUP BY userID;

## MIN(), MAX() ##
# 가장 키가 큰 회원과 가장 키가 작은 회원의 이름과 키 출력
# 에러
SELECT userName, MAX(height), MIN(height) FROM userTBL;
# 수정
SELECT userName, height FROM userTBL 
WHERE height = (SELECT MAX(height) FROM userTBL) OR height = (SELECT MIN(height) FROM userTBL);

## COUNT() ##
SELECT COUNT(mobile1) AS '휴대폰이 있는 사용자' FROM userTBL;
SELECT COUNT(*) FROM userTBL WHERE height >= (SELECT height FROM userTBL WHERE userName = '이휘재');

#####################################################
## HAVING ##
# 에러 (WHERE절 안에는 '집계함수' 사용 불가!!)
SELECT userID AS '사용자', SUM(price * amount) AS '총구매액' FROM buyTBL
WHERE SUM(price * amount) > 1000 
GROUP BY userID;
# 수정 (HAVING 뒤에는 '집계함수' 사용 가능)
SELECT userID AS '사용자', SUM(price * amount) AS '총구매액' FROM buyTBL 
GROUP BY userID
HAVING SUM(price * amount) > 1000
ORDER BY 총구매액; # ORDER BY에서는 별칭 사용 가능, but ''따옴표 불가

## WITH ROLLUP ## 총합계 추가
# 각 항목별 합계(소합계)
SELECT groupName, SUM(price*amount) FROM buyTBL
GROUP BY groupName
# 각 항목별 합계(소합계) + 맨마지막 행에 총합계 추가
SELECT groupName, SUM(price*amount) FROM buyTBL
GROUP BY groupName
WITH ROLLUP;
# 각 num별 합계(소합계) + 그룹별 합계(중간합계) + 총합계
SELECT num, groupName, SUM(price * amount) AS '비용' FROM buyTBL
GROUP BY groupName, num
WITH ROLLUP;
```

---

<aside>
💡

### SELECT 문 내에서 각 절의 위치

SELECT col_name
FROM table_name
[WHERE where_condition]
[GROUP BY {col_name | expr | position}]
[HAVING where_condition]
[ORDER BY {col_name | expr | position}]
[LIMIT n];

</aside>

---

<aside>
💡

### 집계 함수

- SUM()
- AVR()
- MIN()
- MAX()
- COUNT()                     행 개수
- COUNT(DISTINCT)    행 개수(중복x)
- VAR_SAMP()              분산
- STDDEV()  or STD()   표준편차
</aside>

---

<aside>
💡

### 집계함수

- 가능
    - 단순 전체 합계 (집계함수만 쓸 때)
        
        ```sql
        SELECT SUM(amount) FROM pivotTest;
        ```
        
    - 그룹별 합계 with GROUP BY (일반 컬럼 + 집계함수)
        
        ```sql
        SELECT uName, SUM(amount) FROM pivotTest GROUP BY uName;
        ```
        
- 불가능
    - 일반 컬럼 + 집계함수는 GROUP BY 없이 사용 불가!
        
        ```sql
        SELECT uName, SUM(amount) FROM pivotTest;
        ```
        
    - ORDER BY, WHERE, OVER 절 안에 SUM 사용 불가!
        
        ```sql
        SELECT ROW_NUMBER() OVER (ORDER BY SUM(amount)) FROM pivotTest; 
        ```
        
</aside>
