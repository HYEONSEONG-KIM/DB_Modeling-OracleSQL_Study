# SQL문법

## SQL이란?
- Structed Query Language : 구조화된 질의 언어
- DDL(Data Definition Language) : 데이터 정의어(DB 구조 또는 스키마 정의)
    - CREATE(개체 생성)
    - ALTER(개체 변경)
    - DROP(개체 삭제) - 구조자체가 삭제
- DML(Data Manipulation Language) : 데이터 조작어
    - INSERT(데이터 입력)
    - UPDATE(데이터 수정)
    - DELETE(데이터 삭제) - 구조안의 데이터가 삭제
    - SELECT(데이터 검색)
- DCL(Data Control Language) : 데이터 제어어
    - GRANT(권한 부여)
    - REVOKE(권한 회수)
- TCL(Transaction Contorl Language) : 트랜잭션 제어어
    - COMMIT(트랜잭션 적용) - 변화를 하겠다
    - ROLLBACK(마지막 COMMIT시점으로 회귀) - 변화를 하지않고 다시 돌아가겠다
    - SAVEPOINT(임시저장)
- 트랜잭션 : 데이터베이스를 수정하기위해 수행 되어야 할 논리적 단위


## Datatpye(크기)
- 숫자 : NUMBER(자릿수,소수점 자릿수)-max 38자리
- 고정길이 문자 : CHAR - max 2000byte -> Update시 편이
- 가변길이 문자 : VARCHAR2 - 한글 1글자 : 3btye,max 4000byte -> Update시 불편
    + 남은 공간을 어떤식으로 처리하느냐에 따라 달라짐(char는 공백이 남아있고, varchar는 공백을 반납)
- 날짜 : DATE
- 빈 공간을 허용 하지 않으면 N.N(Not Null) - Mandatory(필수)
- 빈 공간을 허용 하면 아무것도 기입하지 않음 - Optional(선택)


## DDL
- CREATE : 구조(객체) 생성
    - CREATE TABLE {테이블명} (
        <속성 ID> <타입>(크기) <NULL여부>,
        ....
        CONSTRAINT {제약어} PRIMARY KEY(기본 키)
    );
- ALTER : 구조 변경
    - ALTER TABLE <테이블명> ADD(Constraint 인덱스키명 Primary Key(필드명1,필드명2), Constraint 외부키명 Foreign key (필드명2) References 외부테이블명(외부필드명)  );  -> 키설정
    - ALTER TABLE :    
        - FIELD 및 변경
        - INDEX 또는 FOREIGN KEY 변경
        - CHECK Option 변경
    - ADD : 추가(FIELRD, KEY, CHECK)
    - MODIFY : 변경(FIELD속성)
        - NOT NULL 인상태에서 NOT NULL 추가하여 코드작성하면 에러
    - DROP : 삭제(FIELD, KEY, CHECK)
- DROP : 데이터 삭제 및 구조 삭제
    - ROLLBACK 불가
- TRUNCATE : 데이터 삭제
    - ROLLBACK 불가
- 오라클에서는 DDL 의경우 자동 commit

### INDEX
- 검색속도가 빨라지게 해주는 자료구조
- SELECT 할 때 인덱스를 생성시 설정했던 묶어놓은 속성들을 검색할때 사용

## DML
- INSERT : 데이어 삽입, INTO : 삽입될 테이블 지정
    - INSERT INTO <테이블명>(속성) VALUES(넣을 값들);
- SELECT : 데이터 조회
    - SELCET {DISTINCT-중복제거} <데이터목록> FROM <테이블 목록> WHERE <검색조건>;
    - GROUP BY <열목록> : 집계할 때 사용(SUM,AVG,MAX,MIN,COUNT)
    - HAVING<검색조건> : 집계후 생성
    - ORDER BY <열목록> : 정렬
    - 애스터리스크(*) 는 모든 속성
    - ALIAS : 속성뒤에 AS (속성명) 으로 컬럼헤딩을 (속성명)으로 변경 or "속성명"으로 AS를 생략해도 가능 or AS "" 생략가능
- UPDATE : 데이터 수정
    - UPDATE <테이블명 >SET <필드명1 = 값1, 필드명2 = 값2...>WHERE <검색조건>
    - UPDATE : 갱신하고자 하는 테이블 지정
    - SET : 새로운 데이터 갱신
    - WHERE : 갱신하기 원하는 데이터의 검색 조건(행 필터)
    - 반드시 WHERE 조건 넣기
- DELETE : 데이터 삭제
    - ROLLBAKC 가능


### CRUD
- C : CREAT (INSERT)
- R : READ (SELECT)
- U : UPDATE(UPDATE)
- D : DELETE(DELETE)

## 데이터 정렬
- ROW를 Sort하고자 하면 ORDER BY 절을 사용
- ASC(ASCENDING) : ORDER BY (정렬하고자 하는 컬럼명) ASC -> 오름차순 정렬
- DESC(DESCENDING) : ORDER BY (정렬하고자 하는 컬럼명) DESC -> 내림차순 정렬
- DEAULT 는 오름차순 정렬
- ALIAS로 정렬 가능
- 입력한 컬럼의 번호로 정렬 가능
    - EX)SELECT MEM_ID, MEM_NAME FROM MEMBER ORDER BY 2 ASC; => 2번째인 MEM_NAME으로 오름차순 정렬
- ORDER BY 1,2 => 1의 정렬된 값이 동일 할때 같은 그룹끼리 2의 값으로 2차로 정렬
- 중복제거후 정렬 하고 싶으면 DISTINCT 함께 사용
    - SELECT DISTINCT 1,2 => 1+2 로 보고 중복 제거
- 정렬은 항상 맨마지막

## WHERE
- SELECT시 비교연산,논리연산을 통해 검색 조건을 설정(행,ROW)
- 비교 연산자
    - = 같다
    - <>, != 같지않다
    - <,> 크다 작다
    - <=,>= 크거나 같다 작거나 같다
- 논리 연산자
    - AND 모두가 참이어야 참(점으로 표기)
    - OR 하나라도 참이면 참 (+로 표기)
    - NOT(조건) 조건이 거짓이면 참(위에 선하나)
    - 우선순위 : (), NOT, AND, OR
- IN : 질의 탐색을 위해 사용될 둘이상의 표현식을 지정(OR연산자가 여러개)
    - EX)회원의 아이디가 C1 C4 C6 인 회원을 찾음 -> WHERE MEM_ID IN('C1', 'C4', 'C6');
- (NOT A) AND (NOT B) 와 NOT(A OR B)는 같음(드모르간의 정리)
- 연산시 자료형이 같아야 함
- 만약 문자형 (비교연산) 숫자 를 비교하면 문자형이 숫자형으로 자동 형변환
- 서브쿼리 : 쿼리안에 사용된 또라는 select문