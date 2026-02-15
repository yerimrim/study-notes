```sql
# 테이블 불러오기
SELECT * FROM memberTBL;

# 특정 열만 불러오기
SELECT memberName, memberAddress FROM memberTBL;

# 특정 행만 불러오기
SELECT * FROM memberTBL WHERE memberName = '토마스';
#####################################################
# 테이블 생성 (테이블 이름에 띄어쓰기 포함시 `` 사용 ('' 사용 x))
CREATE TABLE `my testTBL` (id INT);
#####################################################
# 테이블 생성
CREATE TABLE indexTBL(first_name varchar(14), last_name varchar(16), hire_date date);
INSERT INTO indexTBL
		SELECT first_name, last_name, hire_date
        FROM employees.employees
        LIMIT 500;
SELECT * FROM indexTBL;

# 특정 사람에 대한 정보만 물러오기
SELECT * FROM indexTBL WHERE first_name = 'Mary';
#####################################################
## 인덱스 설정 => 찾는 시간이 줄어듦
CREATE INDEX idx_indexTBL_firstname ON indexTBL(first_name);
# 인덱스로 데이터 조회
SELECT * FROM indexTBL WHERE first_name = 'MARY';
#####################################################
## 뷰어 설정 및 불러오기
# 특정 열만 선택된 뷰어 설정
CREATE VIEW uv_memberTBL
AS
	SELECT memberName, memberAddress FROM memberTBL;
	
# 위에서 선택된 열만 보임
SELECT * FROM uv_memverTBL;
#####################################################
## 스토어드 프로시저 생성 (자주 쓰는 문장 반복 입력을 피하기 위해)
# DELIMITER //는 ;을 //로 치환 => ;에서 실행이 끝나지 않음
# DELEMITER ;는 다시 ;로 치환
DELIMITER //
CREATE PROCEDURE myProc()
BEGIN
	SELECT * FROM memberTBL WHERE memberName = '토마스';
	SELECT * FROM productTBL WHERE productName = '냉장고';
END //
DELIMITER ;

CALL myProc();
#####################################################
## INSERT (데이터 삽입)
INSERT INTO memberTBL VALUES('Soccer', '흥민', '서울시 서대문구 북가좌동');
# 확인
SELECT * FROM memberTBL
#####################################################
## UPDATE (데이터 수정)
UPDATE memberTBL SET memberAddress = '서울 강남구 역삼동' WHERE memberName = '흥민';
# 확인
SELECT * FROM memberTBL;
#####################################################
## DELETE (데이터 삭제)
DELETE FROM memberTBL WHERE memberName = '흥민';
#확인
SELECT * FROM memberTBL;
#####################################################
## 트리거(Trigger): 삭제된 데이터를 자동 저장
# 삭제한 데이터를 저장할 테이블 생성
CREATE TABLE deletedmemberTBL
(memberID char(8),
	memberName char(5),
    memberAddress char(20),
    deletedDate date
);

# 삭제한 데이터를 deletedmemberTBL로 이동하도록 하는 함수 생성
CREATE TABLE deletedmemberTBL
(memberID char(8),
	memberName char(5),
    memberAddress char(20),
    deletedDate date
);

# 자동 기록 트리거 생성
DELIMITER //
CREATE TRIGGER trg_deletedMemberTBL
	AFTER DELETE
    ON memberTBL
    FOR EACH ROW
BEGIN
	INSERT INTO deletedMemberTBL
		VALUES (OLD.memberID, OLD.memberName, OLD.memberAddress,   #기존 MemebrTBL에 있는 데이터 
CURDATE());
END //
DELIMITER ;

# memeberTBL에 새로운 데이터를 삽입했다가 다시 삭제하기
INSERT INTO memberTBL VALUES('Soccer', '흥민', '서울시 서대문구 북가좌동');
DELETE FROM memberTBL WHERE memberName = '흥민';

# memberTBL에서 삭제한 데이터가 deletedmemberTBL에 저장되었는지 확인
SELECT * FROM deletedmemberTBL;
```
