<aside>
💡

### 내부조인

- 2개 이상의 테이블을 묶어서 하나의 결과 테이블을 만드는 것
- 구조
    
    SELECT <열 목록>
    FROM <첫 번째 테이블>
    INNER JOIN <두 번째 테이블>
    ON <조인될 조건>
    [WHERE 검색조건];
    
    ```sql
    ## 1:N 관계
    # userTBL + buyTBL (userID가 같은 사람에 대해서만)
    SELECT * FROM userTBL
    INNER JOIN buyTBL
    ON buyTBL.userID = userTBL.userID;
    # buyTBL + userTBL (userID가 같은 사람에 대해서만)
    SELECT * FROM buyTBL
    INNER JOIN userTBL
    ON buyTBL.userID = userTBL.userID;
    
    # userID가 같은 사람들 중 이름이 KYM인 사람에 대해서만 buyTBL + userTBL
    SELECT * FROM buyTBL
    INNER JOIN userTBL
    ON buyTBL.userID = userTBL.userID
    WHERE buyTBL.userID = 'KYM';
    ###############################################################
    # ERROR (어느 테이블의 userID를 추출할지 명시되지 않음) (userTBL, buyTBL 모두 userID를 가지고 있기 때문)
    SELECT userID, userName, prodName, addr, CONCAT(mobile1, mobile2) AS '연락처'
    FROM buyTBL
    INNER JOIN userTBL
    ON buyTBL.userId = userTBL.userID;
    # userID를 불러올 테이블 명시 (userTBL로 명시해도 같은 결과)
    SELECT buyTBL.userID, userName, prodName, addr, CONCAT(mobile1, mobile2) AS '연락처'
    FROM buyTBL
    INNER JOIN userTBL
    ON buyTBL.userId = userTBL.userID;
    ###############################################################
    # userTBL => U, buyTBL => B로 설정
    SELECT B.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
    FROM buyTBL B
    INNER JOIN userTBL U
    ON B.userID = U.userID;
    
    # 컬럼 순서를 명시했으므로 아래와 같은 결과 출력
    SELECT B.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
    FROM buyTBL B
    INNER JOIN userTBL U
    ON B.userID = U.userId;
    
    # 컬럼 순서를 명시했으므로 위와 같은 결과 출력
    SELECT U.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
    FROM userTBL U
    INNER JOIN buyTBL B
    ON U.userID = B.userID;
    ###############################################################
    ## ORDER BY
    SELECT U.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
    FROM userTBL U
    INNER JOIN buyTBL B
    ON U.userID = B.userID
    ORDER BY U.userID;
    
    ## DISTICT
    SELECT DISTINCT U.userID, U.userName, U.addr
    FROM userTBL U
    INNER JOIN buyTBL B
    ON U.userID = B.userID
    ORDER BY U.userID;
    # 위와 같음
    SELECT DISTINCT U.userID, U.userName, U.addr
    FROM buyTBL B
    INNER JOIN userTBL U
    ON U.userID = B.userID
    ORDER BY U.userID;
    
    ## WHERE EXISTS (조건을 만족하는 행의 유무에 대해서만 확인)
    
    # 중복 x (userTBL의 userID에는 중복이 없으므로 중복 없이 출력)
    SELECT * FROM userTBL
    WHERE EXISTS (SELECT * FROM buyTBL WHERE userTBL.userID = buyTBL.userID);
    # 중복 o (buyTBL에 대해서 선택 => buyTBL에는 userID 중복이 존재)
    SELECT * FROM buyTBL
    WHERE EXISTS (SELECT * FROM userTBL WHERE userTBL.userID  = buyTBL.userID);
    
    # 중복 x (userTBL의 userID에는 중복이 없으므로 중복 없이 출력)
    SELECT U.userID, U.userName, U.addr
    FROM userTBL U
    WHERE EXISTS(SELECT * FROM buyTBL B WHERE U.userID = B.userID);
    # error (선택 column을 buyTBL에 대해서만 설정 가능)
    SELECT U.userID, U.userName, U.addr
    FROM buyTBL B
    WHERE EXISTS(SELECT * FROM userTBL U WHERE U.userID = B.userID);
    # 중복 o (buyTBL에 대해서 선택 => buyTBL에는 userID 중복이 존재)
    SELECT B.userID, B.prodName FROM buyTBL B
    WHERE EXISTS(SELECT * FROM userTBL U WHERE U.userID = B.userID);
    ###############################################################
    ###############################################################
    ## N:N 관계
    # 테이블 생성
    CREATE TABLE stdTBL
    (stdName VARCHAR(10) NOT NULL PRIMARY KEY,
    addr CHAR(4) NOT NULL);
    CREATE TABLE clubTBL
    (clubName VARCHAR(10) NOT NULL PRIMARY KEY,
    roomNo CHAR(4) NOT NULL);
    CREATE TABLE stdclubTBL
    (num int AUTO_INCREMENT NOT NULL PRIMARY KEY,
    stdName VARCHAR(10) NOT NULL,
    clubName VARCHAR(10) NOT NULL,
    FOREIGN KEY (stdName) REFERENCES stdTBL(stdName),
    FOREIGN KEY (clubName) REFERENCES clubTBL(clubName));
    
    # 세 개의 테이블 조인, 학생 이름 순으로 정렬
    SELECT S.stdName, S.addr, C.clubName, C.roomNo
    FROM stdTBL S
    INNER JOIN stdclubTBL SC
    ON S.stdName = SC.stdName
    INNER JOIN clubTBL C
    ON SC.clubName = C.clubName
    ORDER BY S.stdName;
    
    # 세 개의 테이블 조인, 동아리 이름 순으로 정렬
    SELECT C.clubName, C.roomNo, S.stdName, S.addr
    FROM stdTBL S
    INNER JOIN stdclubTBL SC
    ON SC.stdName = S.stdName
    INNER JOIN clubTBL C
    ON SC.clubName = C.clubName
    ORDER BY C.clubName;
    ```
    
</aside>

<aside>
💡

### 외부조인

- 조인 조건을 만족하지 않는 행까지 포함하여 출력하는 조인
- 구조
    
    SELECT <열 목록>
    FROM <첫 번째 테이블(LEFT 테이블)>
    <LEFT | RIGHT> OUTER JOIN <두 번째 테이블(RIGHT 테이블)>
    ON <조인될 조건>
    [WHERE 검색조건];
    

```sql
# 구매기록이 없는 회원도 출력 (userTBL의 모든 회원 출력)
SELECT U.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
FROM userTBL U
LEFT OUTER JOIN buyTBL B
ON U.userID = B.userID
ORDER BY U.userID;
# 같은 결과 (기준 변경)
SELECT U.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
FROM buyTBL B
RIGHT OUTER JOIN userTBL U
ON U.userID = B.userID
ORDER BY U.userID;

# 구매기록이 없는 회원만 출력 (userTBL에는 있으나, buyTBL의 prodName이 없는 사람 출력
SELECT U.userID, U.userName, B.prodName, U.addr, CONCAT(U.mobile1, U.mobile2) AS '연락처'
FROM userTBL U
LEFT OUTER JOIN buyTBL B
ON U.userID = B.userID
WHERE B.prodName IS NULL
ORDER BY U.userID;

###############################################################
# 세 개의 테이블 외부 조인 => 모든 회원들의 정보 출력 (동아리가 없는 학생도 출력)
SELECT S.stdName, S.addr, C.clubName, C.roomNo
FROM stdTBL S
LEFT OUTER JOIN stdclubTBL SC
ON S.stdName = SC.stdName
LEFT OUTER JOIN clubTBL C
ON SC.clubName = C.clubName
ORDER BY S.stdName;

# clubTBL의 clubName을 기준으로 출력하되, 아무도 가입하지 않은 club은 NULL로 출력됨
SELECT C.clubName, C.roomNo, S.stdName, S.addr
FROM stdTBL S
LEFT OUTER JOIN stdclubTBL SC
ON SC.stdName = S.stdName
RIGHT OUTER JOIN clubTBL C
ON SC.clubName = C.clubName
ORDER BY C.clubName;
###############################################################
# 완전 조인
# stdTBL, stdclubTBL, clubTBL 모두 포함
SELECT S.stdName, S.addr, C.clubName, C.roomNo
FROM stdTBL S
LEFT OUTER JOIN stdclubTBL SC
ON S.stdName = SC.stdName
LEFT OUTER JOIN clubTBL C
ON SC.clubName = C.clubName
UNION
SELECT S.stdName, S.addr, C.clubName, C.roomNo
FROM stdTBL S
LEFT OUTER JOIN stdclubTBL SC
ON SC.stdName = S.stdName
RIGHT OUTER JOIN clubTBL C
ON SC>clubName = C.clubName;

```

</aside>

<aside>
💡

### 상호조인

- 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인하는 것 (모든 조합 생성)
- 테이블 행의 수 = 두 테이블의 행의 수의 곱

```sql

# buyTBL + userTBL
SELECT * FROM buyTBL
CROSS JOIN userTBL;

# userTBL + buyTBL
SELECT * FROM userTBL
CROSS JOIN buyTBL;

## COUNT(*)
# 행의 개수 (10 x 12 = 120)
SELECT COUNT(*) AS '데이터개수' FROM userTBL
CROSS JOIN buyTBL;
```

</aside>

<aside>
💡

### 자체조인

- 자기 자신과 자기 자신을 조인하는 것

```sql
# 테이블 생성
CREATE TABLE empTBL(emp CHAR(3), manager CHAR(3), empTel VARCHAR(8));
INSERT INTO empTBL VALUES ('나사장', NULL, '0000');
INSERT INTO empTBL VALUES ('김재무', '나사장', '2222');
INSERT INTO empTBL VALUES ('김부장', '김재무', '2222-1');
INSERT INTO empTBL VALUES ('이부장', '김재무', '2222-2');
INSERT INTO empTBL VALUES ('우대리', '이부장', '2222-2-1');
INSERT INTO empTBL VALUES ('지사원', '이부장', '2222-2-2');
INSERT INTO empTBL VALUES ('이영업', '나사장', '1111');
INSERT INTO empTBL VALUES ('한과장', '이영업', '1111-1');
INSERT INTO empTBL VALUES ('최정보', '나사장', '3333');
INSERT INTO empTBL VALUES ('윤차장', '최정보', '3333-1');
INSERT INTO empTBL VALUES ('이주임', '윤차장', '3333-1-1');

# A.emp가 '우대리'인 경우, manager를 B.emp에 저장, B.empTel은 B.emp의 연락처
SELECT 
	A.emp AS '부하직원', 
	B.emp AS '직속상관', 
	B.empTel AS '직속상관연락처'
FROM empTBL A
INNER JOIN empTBL B
ON A.manager = B.emp
WHERE A.emp = '우대리';

```

</aside>

<aside>
💡

### UNION / UNION ALL

- 두 쿼리의 결과를 행으로 합치는 연산자
- UNION (중복 제거) / UNION ALL (중복 포함)
- 구조
    
    SELECT 문장1
    UNION [ALL]
    SELECT 문장2
    

```sql
# 한 행에 stdName, clubName 결합 (중복된 행 제거)
SELECT stdName FROM stdclubTBL
UNION
SELECT clubName FROM stdclubTBL;

# 한 행에 stdName, clubName 결합 (중복 행 제거 x)
SELECT stdName FROM stdclubTBL
UNION
SELECT clubName FROM stdclubTBL;
```

</aside>

<aside>
💡

### NOT IN / IN

- NOT IN: 첫 번째 쿼리의 결과 중에서 두 번째 쿼리에 해당하는 것을 제외하고 출력
- IN: 해당 값이 목록에 있을 시 출력

```sql
# userName + 전화번호 (전화번호가 없는 사람 제외하고 출력)
SELECT userName, CONCAT(mobile1, '-', mobile2) AS '전화번호' FROM userTBL
WHERE userName NOT IN (SELECT userName FROM userTBL WHERE mobile1 IS NULL);

# userName + 전화번호 (전화번호가 없는 사람만 출력)
SELECT userName, CONCAT(mobile1, '-', mobile2) AS '전화번호' FROM userTBL
WHERE userName IN (SELECT userName FROM userTBL WHERE mobile1 IS NULL);
```

</aside>

<aside>
💡

### 스토어드 프로시저

- 구조
    
    DELIMITER $$
    CREATE PROCEDURE 스토어드프로시저이름()
    BEGIN
    이곳에 SQL 프로그래밍 코딩
    END $$
    DELIMITER ;
    CALL 스토어드프로시저이름();
    
</aside>

<aside>
💡

### **IF … ELSE … END IF 문**

- 구조
    
    IF <불 표현식> THEN
    SQL문장들1 …
    ELSE
    SQL문장들2 …
    END IF;
    
    ```sql
    # ifProc라는 프로시저가 이미 있으면 삭제
    DROP PROCEDURE IF EXISTS ifProc;
    
    # ifProc라는 프로시저 생성
    DELIMITER $$
    CREATE PROCEDURE ifProc()
    BEGIN
    DECLARE var1 INT;
    SET var1 = 100;
    
    IF var1 = 100 THEN
    SELECT '100입니다.';
    ELSE
    SELECT '100이 아닙니다.';
    END IF;
    END $$
    DELIMITER ;
    
    # ifProc 프로시저 불러오기
    CALL ifProc();
    
    ###############################################################
    # ifProc2라는 프로시저가 이미 있으면 삭제
    USE employees;
    DROP PROCEDURE IF EXISTS ifProc2;
    
    # ifProc2 프로시저 생성
    DELIMITER $$
    CREATE PROCEDURE ifProc2()
    BEGIN
    DECLARE hireDate DATE;
    DECLARE curDate DATE;
    DECLARE days INT;
    
    SELECT hire_date INTO hireDate
    FROM employees.employees
    WHERE emp_no = 10001;
    
    SET curDate = CURRENT_DATE();
    SET days = DATEDIFF(curDate, hireDate);
    
    IF (days/365) = 5 THEN
    SELECT CONCAT('입사한 지 ', days, '일이나 지났습니다. 축하합니다.') AS '메시지';
    ELSE 
    SELECT CONCAT('입사한 지 ', days, '일밖에 안되었네요. 열심히 일하세요.') AS '메시지';
    END IF;
    END $$
    DELIMITER ;
    
    # ifProc2 프로시저 불러오기
    CALL ifProc2();
    
    ###############################################################
    # ifProc3라는 프로시저가 이미 있으면 삭제
    DROP PROCEDURE IF EXISTS ifProc3;
    
    # ifProc3 프로시저 생성
    DELIMITER $$
    CREATE PROCEDURE ifProc3()
    BEGIN
    DECLARE point INT;
    DECLARE credit CHAR(1);
    SET point= 77;
    
    IF point >= 90 THEN
    SET credit = 'A';
    ELSEIF point >= 80 THEN
    SET credit = 'B';
    ELSEIF point >= 70 THEN
    SET credit = 'C';
    ELSEIF point >= 60 THEN
    SET credit = 'D';
    ELSE
    SET credit = 'F';
    END IF;
    SELECT CONCAT('취득점수==>', point), CONCAT('학점==>', credit);
    END $$
    DELIMITER ;
    
    # ifProc3 프로시저 불러오기
    CALL ifProc3();
    ```
    
</aside>

<aside>
💡

### CASE 문

```sql
# caseProc이라는 프로시저가 이미 있으면 삭제
DROP PROCEDURE IF EXISTS caseProc;

# caseProc 프로시저 생성
DELIMITER $$
CREATE PROCEDURE caseProc()
BEGIN 
DECLARE point INT;
DECLARE credit CHAR(1);
SET point = 77;

CASE
WHEN point >= 90 THEN
SET credit = 'A';
WHEN point >= 80 THEN
SET credit = 'B';
WHEN point >= 70 THEN
SET credit = 'C';
WHEN point >= 60 THEN
SET credit = 'D';
ELSE
SET credit = 'F';
END CASE;

SELECT CONCAT('취득점수==>', point), CONCAT('학점==>', credit);
END $$
DELIMITER ;

# caseProc 프로시저 불러오기
CALL caseProc();
```

</aside>

<aside>
💡

### CASE문 활용

```sql
SELECT userID, SUM(price*amount) AS '총구매액' FROM buyTBL
GROUP BY userID
ORDER BY SUM(price*amount) DESC;

## INNER JOIN
SELECT B.userID, U.userName, SUM(price * amount) AS '총구매액'
FROM buyTBL B
INNER JOIN userTBL U
ON B.userID = U.userID
GROUP BY B.userID, U.userName
ORDER BY SUM(price * amount) DESC

## OUTER JOIN 
SELECT B.userID, U.userName, SUM(price * amount) AS '총구매액'
FROM buyTBL B
RIGHT OUTER JOIN userTBL U
ON B.userID = U.userID
GROUP BY B.userID, U.userName
ORDER BY SUM(price * amount) DESC;
# OUTER JOIN 기준 변경
SELECT U.userID, U.userName, SUM(price * amount) AS '총구매액'
FROM buyTBL B
RIGHT OUTER JOIN userTBL U
ON B.userID = U.userID
GROUP BY U.userID, U.userName
ORDER BY SUM(price * amount) DESC;

## CASE문
SELECT R.customer_id, 
	   SUM(O.sales),
	   CASE WHEN (SUM(O.sales)>=1000000) THEN '최우수고객'
		      WHEN (SUM(O.sales)>=300000) THEN '우수고객'
          WHEN (SUM(O.sales)>=100000) THEN '일반고객'
          ELSE '유령고객'
	   END AS '고객등급'
FROM order_info O
LEFT OUTER JOIN reservation R
ON O.reserv_no = R.reserv_no
GROUP BY R.customer_id
ORDER BY SUM(O.sales) DESC;
```

</aside>

<aside>
💡

### WHILE, ITERATE, LEAVE

- WHILE문
    
    WHILE () DO
    …
    END WHILE;
    

```sql
DROP PROCEDURE IF EXISTS whileProc;
## 1부터 100까지 합
DELIMITER $$
CREATE PROCEDURE whileProc()
BEGIN
	DECLARE i INT;
    DECLARE hap INT;
    SET i=1;
    SET hap=0;
    
    WHILE (i<=100)DO
		SET hap=hap+i;
        SET i=i+1;
	END WHILE;
    
    SELECT hap;
END $$
DELIMITER ;

CALL whileProc();

## ITERATE, LEAVE
DROP PROCEDURE IF EXISTS whileProc2;

DELIMITER $$
CREATE PROCEDURE whileProc2()
BEGIN
	DECLARE i INT;
    DECLARE hap INT;
    SET i=1;
    SET hap=0;
    
    myWhile: WHILE(i<=100) DO
		IF(i%7=0) THEN
			SET i=i+1;
            ITERATE myWhile;
		END IF;
		SET hap=hap+i;
		IF (hap>1000) THEN
			LEAVE myWhile;
		END IF;
    
		SET i=i+1;
	END WHILE;
    
    SELECT hap;
END $$
DELIMITER ;

CALL whileProc2();
```

</aside>

<aside>
💡

### 오류 처리 형식

```sql
## error 출력
DROP PROCEDURE IF EXISTS errorProc;
DELIMITER $$
CREATE PROCEDURE errorProc()
BEGIN
	DECLARE CONTINUE HANDLER FOR 1146 SELECT '테이블이 없어요ㅠㅠ' AS '메시지';
    SELECT * FROM noTable;
END $$
DELIMITER ;
CALL errorProc();

DROP PROCEDURE IF EXISTS errorProc2;
DELIMITER $$
CREATE PROCEDURE errorProc2()
BEGIN
DECLARE CONTINUE HANDLER FOR SQLEXCEPTION
BEGIN
SHOW ERRORS;
SELECT ‘오류가 발생했네요. 작업은 취소시켰습니다.’ AS ‘메시지’;
ROLLBACK;
END;
INSERT INTO userTBL VALUES(‘YJS’, ‘윤정수’, 1988, ‘서울’, NULL, NULL, 170, CURRENT_DATE());
END $$
DELIMITER ;
CALL errorProc2();
```

</aside>

<aside>
💡

### 동적할당

```sql
USE cookDB;
PREPARE myQuery FROM 'SELECT * FROM userTBL WHERE userID = "NHS"';
EXECUTE myQuery;
DEALLOCATE PREPARE myQuery;

USE cookDB;
DROP TABLE IF EXISTS myTable;
CREATE TABLE myTable (id INT AUTO_INCREMENT PRIMARY KEY, mDate DATETIME);
SET @curDATE = CURRENT_TIMESTAMP();
PREPARE myQuery FROM 'INSERT INTO myTable VALUES(NULL, ?)';
EXECUTE myQuery USING @curDATE;
DEALLOCATE PREPARE myQuery;
SELECT * FROM myTable;
```

</aside>
