<aside>
💡

### 데이터 형식

- 숫자 데이터 형식
    - SMALLINT: 2byte, 정수
    - INT: 4byte, 정수
    - BIGINT: 8byte, 정수
    - FLOAT: 4byte, 소수점 아래 7자리까지
    - DOUBLE: 8byte, 소수점 아래 15자리까지
    - DECIMAL(m,[d]): 5~17byte, 전체 자릿수 m, 소수점 아래 자릿수 d
- 문자 데이터 형식
    - CHAR(n): n=1~255, UTF-8
    - VARCHAR(n): n=1~65535, UTF-8
    - LONGTEXT: 글자가 길어지면 VARCHAR 대신 사용
    - LONGBLOB: 대용량
- 날짜와 시간 데이터 형식
    - DATE: 3byte, YYYY-MM-DD 형식
    - DATETIME: 8byte, YYYY-MM-DD HH:MM:SS 형식
- 데이터 형식 변환 함수: CAST(), CONVERT()
    - CAST(expression AS 데이터형식 [(길이)])
    CONVERT(expression, 데이터형식 [(길이)])
</aside>

---

### 내장 함수

<aside>
💡

### 데이터 형식 변환 함수

```sql
## CAST(expression AS 데이터형식), CONVERT(expression, 데이터형식) ##
# DATE는 날짜만 출력
SELECT CAST('2027-10-19 12:35:29.123' AS DATE) AS 'DATE';
# TIME은 시간만 출력 (소수점 아래 반올림)
SELECT CAST('2027-10-19 12:35:29.123' AS TIME) AS 'TIME';
# 날짜 시간 모두 출력 (소수점 아래 반올림)
SELECT CAST('2027-10-19 12:35:29.123' AS DATETIME) AS 'DATETIME';
# 시간은 00:00:00으로 출력됨
SELECT CAST('2027-10-19' AS DATETIME) AS 'DATETIME';
# 날짜가 없으므로 NULL 출력
SELECT CAST('10:10:33' AS DATETIME) AS 'DATETIME';
# $을 -으로 바꿔서 DATE 형식으로 출력
SELECT CAST('2020$12$12' AS DATE);
# CONVERT를 활용해 DATETIME 형식으로 출력
SELECT CONVERT('2020-02-02 12:32:32.23', DATETIME);

# 평균 구매 개수
SELECT AVG(amount) AS '평균 구매 개수' FROM buyTBL;
# CAST를 활용해 평균 구매 개수를 정수형으로 출력 (반올림)
SELECT CAST(AVG(amount) AS SIGNED INTEGER) AS '평균 구매 개수 (정수형)' FROM buyTBL;
# CONVERT를 활용해 평균 구매 개수를 정수형으로 출력 (반올림)
SELECT CONVERT(AVG(amount), SIGNED INTEGER) AS '평균 구매 개수 (정수형)' FROM buyTBL;

## SET, SELECT ##
SET @myVar1 = 5; # myVa1에 숫자 5 입력
SELECT @myVar1; # 출력: 5

SET @myVar2 = 3; # myVar2에 숫자 3
SET @myVar3 = 4.25; # myVar3에 숫자 4.25 입력
SELECT @myVar2 + @myVar3; # 출력: 7.250000000

SET @myVar4 = 'MC ==> '; # myVar4에 'MC ==> '입력
SELECT @myVar4, userName FROM userTBL WHERE height > 170; # @myVar4 열에 MC ==> 출력, userName 열에 height>170인 사람들 이름만 출력

# 출력: 0 (사칙연산 시 문자는 0으로 인식)
SET @a = 'hi', @b = 'hello';
SELECT @a + @b;

# 출력: 6 (사칙연산 시 숫자로 자동 변환)
SET @a = '3', @b = '3';
SELECT @a + @b;

# 출력: 33
SET @a = '3', @b = '3';
SELECT CONCAT (@v1 , @v2);

## PREPARE EXECUTE ## (USING에 숫자 바로 입력 불가!)
# LIMIT을 3으로 해서 userName, height을 출력 (height이 작은 순서로 정렬)
SET @myVar1 = 3;
PREPARE myQuery FROM 'SELECT userName, height FROM userTBL ORDER BY height LIMIT?';
EXECUTE myQuery USING @myVar1;

# 1970년 이후에 태어난 사람의 userName, birthYear 출력
SET @year = 1970;
PREPARE testQuery FROM 'SELECT userName, birthYear FROM userTBL WHERE birthYear > ?';
EXECUTE testQuery USING @year;

## CONCAT ##
# price와 amount를 문자로 받은 후 n x k = 을 '단가x수량'열에 출력
SELECT num,
CONCAT(CAST(price AS CHAR(10)), ' X ', CAST(amount AS CHAR(4)), ' =') AS '단가x수량=',
price * amount AS '구매액'
FROM buyTBL;
# prodName별 단가x수량 출력
SELECT prodName,
CONCAT(CAST(MIN(price) AS CHAR(10)) , ' X ', CAST(SUM(amount) AS CHAR(10))) AS '단가x수량',
MIN(price)* SUM(amount) AS '='
FROM buyTBL
GROUP BY prodName
ORDER BY prodName;

## 암시적인 형 변환 ##
# 문자와 문자를 더함(정수로 변환한 후 처리) (100+200 ⇒ 출력: 300)
SELECT '100' + '200';

# 문자와 문자를 연결(문자열 그대로 처리) (출력: 100200)
SELECT CONCAT('100', '200');

# 정수와 문자를 연결(정수를 문자로 변환하여 처리) (출력: 100200, 100100)
SELECT CONCAT(100, '200');
SELECT CONCAT(100, 100);

# 정수인 3으로 변환한 후 비교 (1>3 ⇒ 출력: 0)
SELECT 1 > '3mega';

# 정수인 3으로 변환한 후 비교 (4>3 ⇒ 출력: 1)
SELECT 4 > '3MEGA';

# 문자가 0으로 변환됨 (0=0 ⇒ 출력: 1)
SELECT 0 = 'mega3';

```

</aside>

<aside>
💡

### 제어 흐름 함수

```sql
## IF(s1,s2,s3) ##
# s1이 참이면 s2, 거짓이면 s3 출력
SELECT IF(100>200, '참', '거짓');

## IFNULL(s1, s2) ##
# s1이 NULL이면 s2 출력
# NULL이 아니면 s1 그대로 출력
SELECT IFNULL(NULL, '널'), IFNULL(100, '널');

## NULLIF(s1, s2) ##
# s1과 s2가 같으면 NULL 출력
# s1과 s2가 다르면 s1 출력
SELECT NULLIF(100,100), NULLIF(200,100);

## SELECT CASE - WHEN - THEN - ELSE - END; ##
# IF-ELSEIF-ELSE문과 동일
SELECT CASE 10
	WHEN 1 THEN '일'
  WHEN 5 THEN '오'
  WHEN 10 THEN '십'
  ELSE '모름'
END;

SET @var1 = 2;
SELECT CASE @var1
WHEN 1 THEN 2
WHEN 2 THEN 4
ELSE 10
END;
```

</aside>

<aside>
💡

### 문자열 함수

```sql
## ASCII(), CHAR() ##
SELECT ASCII('A'); # A의 아스키코드값 65 출력
SELECT CHAR(65); # 아스키코드 값 65에 해당하는 문자인 A 출력

## BIT_LENGTH(), CHAR_LENGTH(), LENGTH() ##
SELECT BIT_LENGTH('abc'); # 비트 수
SELECT LENGTH('abc'); # 바이트 수
SELECT CHAR_LENGTH('abc'); # 문자 개수

## CONCAT(), CONCAT_WS() ##
SELECT CONCAT('2020-','01-','01'); # 연결
SELECT CONCAT_WS('/', '2020', '01', '01'); # 사이에 '/'를 넣어 연결

## ELT(), FIELD(), FIND_IN_SET(), INSTR(), LOCATE() ##
SELECT ELT(2, '하나', '둘', '셋'); # 숫자에 대응하는 위치에 있는 문자 출력

SELECT FIELD('둘', '하나', '둘', '셋'); # (출력값: 2) 찾고자 하는 문자와 같은 것의 위치 출력 (각각의 따옴표로 구분)
SELECT FIND_IN_SET('둘', '하나,둘,셋'); # (출력값: 2) 찾고자 하는 문자와 같은 문자의 위치 출력 (하나의 따옴표 안에서 컴마로 구분)
SELECT FIND_IN_SET('둘', CONCAT_WS(',', '하나', '둘', '셋')); # (출력값: 2)
SELECT FIELD('넷', '하나', '둘', '셋'); # (출력값: 0) 매치되는 문자열 없을 시 0 반환
SELECT FIND_IN_SET('넷', '하나,둘,셋'); # (출력값: 0) 매치되는 문자열 없을 시 0 반환

SELECT INSTR('하나둘셋', '둘'); # (출력값: 3) 문자열에서 찾고자 하는 문자와 같은 것의 위치 출력 (찾고자 하는 문자 나중에 입력, 문자열 따로 입력 x)
SELECT LOCATE('둘', '하나둘셋'); # (출력값: 3) 문자열에서 찾고자 하는 문자와 같은 것의 위치 출력 (찾고자 하는 문자 먼저 입력, 문자열 따로 입력 x)

## FORMAT() ##
SELECT FORMAT(123456.123456, 4); # 소수점 n째 자리까지 출력 (반올림 same as ROUND(), 단 문자열로 반환함)

## BIN(), HEX(), OCT() ##
SELECT BIN(31), HEX(31), OCT(31); # 31의 2, 16, 8 진수 출력

## INSERT() ##
SELECT INSERT('abcdefghi', 3, 4, '****'); # 문자열의 3번 위치부터 문자 4개 삭제, 그 사이에 '****' 입력
SELECT INSERT('abcdefghi', 3, 2, '*'); # 문자열의 3번 위치부터 문자 2개 삭제, 그 사이에 '*' 입력

## LEFT(), RIGHT() ##
SELECT LEFT('abcdefghi', 3); # 문자열의 왼쪽 3개 출력
SELECT LEFT(12465, 3); # 왼쪽 3개 출력 (숫자는 따옴표 생략 가능)
SELECT RIGHT('abcdefghi', 3); # 문자열의 오른쪽 3개 출력

## LOWER(), UPPER() ##
SELECT LOWER('abcdEFGH'); # 문자열 모두 소문자로 변환
SELECT UPPER('abcdEFGH'); # 문자열 모두 대문자로 변환

## LPAD(), RPAD() ##
SELECT LPAD('쿡북', 5, '**'); # 문자열을 5자리로 늘리고, 왼쪽에 '***'으로 채워짐 => ***쿡북
SELECT RPAD('쿡북', 5, '^-^0'); # 문자열을 5자리로 늘리고, 오른쪽에 '^-^'으로 채워짐 => 쿡북^-^
# (채우는 문자열이 공간보다 많은 경우 앞에서 끊김)
# (채우는 문자열이 공간보다 적은 경우 다시 앞부터 반복)

## LTRIM(), RTRIM() ##
SELECT LTRIM(' 쿡북'); # 문자열의 왼쪽 공백 제거
SELECT RTRIM('쿡북 '); # 문자열의 오른쪽 공백 제거

## TRIM(), TRIM(BOTH FROM), TRIM(LEADING FROM), TRIM(TRAILING FROM) ##
SELECT TRIM(' 쿡북 '); # 앞뒤 공백 모두 제거

SELECT TRIM(BOTH 'ㅋ' FROM 'ㅋㅋㅋㅋ재밌어요.ㅋㅋㅋ'); # 앞뒤 'ㅋ' 모두 제거 
SELECT TRIM('ㅋ' FROM 'ㅋㅋㅋㅋ재밌어요.ㅋㅋㅋ'); # 앞뒤 'ㅋ' 모두 제거 

SELECT TRIM(LEADING 'ㅋ' FROM 'ㅋㅋㅋㅋ재밌어요.ㅋㅋㅋ'); # 앞의 'ㅋ' 모두 제거
SELECT TRIM(LEADING 'ㅋㅋㅋ' FROM 'ㅋㅋㅋㅋ재밌어요.ㅋㅋㅋ'); # 앞의 'ㅋㅋㅋ'제거, 앞에서 'ㅋ'하나는 남음 (반복 시행 시 수가 안 맞음)

SELECT TRIM(TRAILING 'ㅋ' FROM 'ㅋㅋㅋㅋ재밌어요.ㅋㅋㅋ'); # 뒤의 'ㅋ' 모두 제거

## REPEAT(), REPLACE(), REVERSE() ##
SELECT REPEAT('쿡북', 3); # 쿡북 3번 연속 출력
SELECT REPLACE('IT 쿡북 MySQL', '쿡북', 'CookBook'); # 주어진 문자열에서 '쿡북'을 'CookBook'으로 변환
SELECT REVERSE('MySQL'); # 거꾸로 출력

## SPACE() ##
SELECT CONCAT('IT', SPACE(5), 'CookBook MySQL'); # 'IT'와 'CookBook MySQL' 사이에 공백 5개 출력

## SUBSTRING(), SUBSTRING_INDEX() ##
SELECT SUBSTRING('대한민국만세', 3, 2); # 왼쪽에서 3번째부터 2개 출력
SELECT SUBSTRING('대한민국만세', -3, 2); # 오른쪽에서 3번째부터 2개 출력
SELECT SUBSTRING_INDEX('www.mysql.com', '.', 2); # 왼쪽에서 두번째 '.'까지 출력
SELECT SUBSTRING_INDEX('www.mysql.com', '.', -2); # 오른쪽에서 두번째 '.'까지 출력 (

```

</aside>

<aside>
💡

### 수학 함수

```sql
## ABS(), CEILING(), FLOOR(), TRUNCATE(), ROUND() ##
SELECT ABS(-100); # 절댓값
SELECT CEILING(4.3); # 올림
SELECT FLOOR(4.7); # 버림

SELECT TRUNCATE(12345.12345, 2); # 소수점 아래 3번째부터 버림, 소수점 아래 2번째까지 출력
SELECT TRUNCATE(12345.12345, -2); # 정수 제일 끝에서 2번째까지 버림, 출력값: 12300

SELECT ROUND(4.5); # 소수점 첫 번째 자리에서 반올림 (정수로 출력)
SELECT ROUND(12345.12645, 2); #  소수점 아래 3번째에서 반올림, 소수점 아래 2번째까지 출력

## RAND(), SIGN() ##
SELECT RAND(); # 0이상 1미만 랜덤 추출
SELECT FLOOR(RAND()*6+1); # 1~6 사이 랜덤 추출 (주사위)
# 양수이면 1, 0이면 0, 음수이면 -1 출력
SELECT SIGN(100), SIGN(0), SIGN(-100.123);

## MOD() ##
# 157을 10으로 나눈 '나머지' 출력
SELECT MOD(157, 10);
SELECT 157%10;
SELECT 157 MOD 10;

## POW(), SQRT() ##
SELECT POW(2,3); # 거듭제곱 (2^3)
SELECT SQRT(9); # 루트 (루트9=3)

## CONV() ## 진수 변환
SELECT CONV('AA', 16, 2); # 'AA'를 16진수에서 2진수로 변환

## DEGREES(), RADIANS(), PI() ##
SELECT PI(); # 파이값 3.14 반환
SELECT DEGREES(PI()); # 파이값의 라디안 -> 각도
SELECT RADIANS(180); # 각도 -> 라디안

## SIN(),COS(),TAN(),ASIN(),ACOS(),ATAN(),ATAN2(n1,n2) ## 삼각함수 값
## EXP(),LN(),LOG(),LOG(밑,진수),LOG2(),LOG10() ## 지수, 로그

```

</aside>

<aside>
💡

### 날짜/시간 함수

```sql
## ADDDATE(), SUBDATE(), ADDTIME(), SUBTIME() ##
# INTERVAL 만큼 날짜 증가
SELECT ADDDATE('2020-01-01', INTERVAL 1 DAY);
SELECT ADDDATE('2020-01-01', INTERVAL 1 MONTH);
SELECT ADDDATE('2020-01-01', INTERVAL 1 YEAR);
# INTERVAL 만큼 날짜 감소
SELECT SUBDATE('2020/01/01', INTERVAL 1 DAY);
SELECT SUBDATE('2020/01/01', INTERVAL 1 MONTH);
# 시간 증가
SELECT ADDTIME('2020-01-01 23:59:59', '0:0:1');
SELECT ADDTIME('22:00:00', '1:1:1');
# 시간 감소
SELECT SUBTIME('2020-01-01 00/00/00', '0:0:1');

## CURDATE()=CURRENT_DATE(), CURTIME()=CURRENT_TIME(), NOW(), SYSTDATE() ##
# CURDATE() - 현재 날짜
# CURTIME() - 현재 시간
# NOW(), SYSDATE() - 현재 날짜 + 시간
SELECT CURDATE(), CURTIME(), NOW(), SYSDATE();

## YEAR(), MONTH(), DAY(), HOUR(), MINUTE(), SECOND(), MICROSECOND() ##
SELECT YEAR(CURRENT_DATE()); # 현재 연도 출력
SELECT MONTH(CURDATE()); # 현재 달 출력
SELECT DAY(CURDATE()); # 현재 일 출력
SELECT HOUR(CURRENT_TIME()); # 현재 시간 출력
SELECT MINUTE(CURTIME()); # 현재 분 출력
SELECT SECOND(CURTIME()); # 현재 초 출력
SELECT MICROSECOND(CURTIME()); # 현재 밀리초 출력

## DATE(), TIME() ##
SELECT DATE(NOW()), TIME(NOW());
SELECT DATE(CURDATE()), TIME(CURTIME());

## DATEDIFF(), TIMEDIFF() ##
# 날짜1-날짜2
SELECT DATEDIFF('2024-01-01', NOW());
SELECT DATEDIFF('2024-01-02 00:00:00', '2024-01-01 23:59:59'); # 날짜만 생각하기 때문에 출력값=1
# 시간1-시간2
SELECT TIMEDIFF('23:23:59', '12:11:10');
SELECT TIMEDIFF('2024-01-01 23:23:23', NOW());

## DAYOFYEAR(), MONTHNAME(), DAYOFMONTH(), DAYOFWEEK() ##
SELECT DAYOFYEAR(CURDATE()); # 365일 중 몇 번째 날인지
SELECT MONTHNAME(CURDATE()); # 몇 월인지 (문자로)
SELECT DAYOFMONTH(CURDATE()); # 몇 일인지 (현재 월에서)
SELECT DAYOFWEEK(CURDATE()); # 요일 (일:1 ~ 토:7)

## QUARTER ##
SELECT QUARTER('2020-07-01'); # 주어진 날짜가 해당하는 '분기' 반환
SELECT QUARTER('2020-07-01 23:00:00'); # 시간 넣어도 됨 (위와 똑같은 출력값)

## TIME_TO_SEC ##
SELECT TIME_TO_SEC('12:11:10'); # 초 단위로 반환

## LAST_DAY ##
SELECT LAST_DAY('2024-02-03'); # 해당 월의 마지막 날짜 반환 (=> 출력값: 2024-02-29)

## MAKEDATE(), MAKETIME() ##
SELECT MAKEDATE(2023, 10); # 해당 연도의 처음부터 숫자만큼 지난 날짜 반환 (=> 출력값: 2023-01-10)
SELECT MAKETIME(12, 10, 10); # 주어진 숫자로 시간 출력 (=> 출력값: 12:10:10)

## PERIOD ADD(연월, 개월 수), PERIOD DIFF(연월1, 연월2) ##
# '-' 구분 x, 연월까지만 입력, ''해도 되고 안 해도 됨
SELECT PERIOD_ADD(202001, 11); # 2020-01에서 11개월 증가한 값 반환
SELECT PERIOD_DIFF('202001', '201812'); # 연월1 - 연월2의 개월 수 반환

```

</aside>

<aside>
💡

### 시스템 정보 함수 (암기 X)

```sql
## USER(), DATABASE(), VERSION() ##
SELECT USER(); # 현재 사용자
SELECT DATABASE(); # 현재 데이터 베이스
SELECT VERSION(); # 현재 버전

## FOUND_ROWS() ##
# 바로 이전에 조회된 행의 개수 출력
USE cookDB;
SELECT * FROM userTBL;
SELECT FOUND_ROWS();

## ROW_COUNT() ##
# 바로 이전의 INSERT, DELETE, UPDATE 된 행의 개수 출력
USE cookDB;
UPDATE buyTBL SET price = price*2;
SELECT * FROM buyTBL;
SELECT ROW_COUNT();

## SLEEP() ##
# 쿼리 실행 잠시 멈춤
SELECT SLEEP(5);
SELECT '5초 후에 이게 보여요.';
```

</aside>
