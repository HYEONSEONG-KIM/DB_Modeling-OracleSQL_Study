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
- Alias 는 정렬에서만 사용가능

## WHERE
- SELECT시 비교연산,논리연산을 통해 검색 조건을 설정(행,ROW)

## 연산자
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
    - (NOT A) AND (NOT B) 와 NOT(A OR B)는 같음(드모르간의 정리)
    - IN : 질의 탐색을 위해 사용될 둘이상의 표현식을 지정(OR연산자가 여러개)
        - EX)회원의 아이디가 C1 C4 C6 인 회원을 찾음 -> WHERE MEM_ID IN('C1', 'C4', 'C6');
- 연산시 자료형이 같아야 함
- 만약 문자형 (비교연산) 숫자 를 비교하면 문자형이 숫자형으로 자동 형변환
- 서브쿼리 : 쿼리안에 사용된 또라는 select문

## 기타 연산자
- BETWEEN : 범위내에 모든 값을 탐색
    - EX) WHERE (컬럼명) BETWEEN A AND B => A와B 사이의 값 모두 출력
    - NOT 사용시 전체 구문앞에 써도 되고, NOT BWTWEEN으로 써도 됨
- LIKE : 컬럼 값을 지정된 패턴과 비교하여 문자형태가 같은 ROW를 검색
    - LKIE와 함께 쓰인 % : 와일드 카드(%를 문자로 인식하지 않음) -> % : 여러글자, _ : 한 글자
    - %AB% : 위치에 상관없이 AB 글자가 모두 포함
    - A% :  앞에 첫 글자가 A(A로 시작하는 문자)
    - %A : 마지막 글자가 A(A로 끝나는 문자)
    - _A% : 앞글자 공백후 A
    - A_ : A로 시작하는 두글자 문자(찾고자 하는 데이터가 두 글자 이상이면 검색 되지 않음)
- & 데이터에 입력하려고 하면 주소 연산자를 참조하라고 함 -> CHR(아스키코드 표 번호) || '데이터'로 입력가능
    - 번호 검색 : SELECT ASCII ('원하는 문자') FROM DUAL;
    - 문자 검색 : SELECT CHR(번호) FROM DUAL;
    - DUAL : 가상의 테이블, DBMS에서 테이블 없이 확인하고자 하는 작업을 수행할때 사용

## 함수
- 미리 만들어 놓은 작은 프로그램으로 혼자서 실행되지 않고 다른 함수에 의해서 호출을 받아야만 실행
- 단일행(Single-row)함수
    - 테이블에 저장되어있는 개별 행을 대상으로 함수를 적용하여 하나의 값 반환
    - SELECT, WHERE, ORDER BY 절에서 사용
    - 함수를 중접하여 사용가능
- 복수행(Multiple-row)함수
    - 여러 행을 그룹화하여 그룹별로 결과를 처리하여 하나의 결과 반환
    - 그룹화하고자 하는 경우 GROUP BY절 사용

### 문자열 함수
- C || C : 둘 이상의 문자열을 연결하는 결합 연산자 (입력한 값 결합)
- CONCAT : 두 문자열을 연결하여 반환
    - ex)SELECT CONCAT('My Name is ',MEM_NAME) FROM MEMBER;
    - => My Name is 김은대
- CHR, ASCII : ASCII값을 문자로, 문자를 ASCII값으로 반환 (코드나 숫자로 반환)
    - ex) SELECT CHR(65) "CHR", ASCII('ABC') "ASCII" FROM DUAL;
    - SELECT CHR(75) "CHR", ASCII('K') "ASCII" FROM DUAL;
    - =>K	75
- LOWER : 해당 문자나 문자열을 소문자로 반환 (소문자로)
- UPPER : 대문자로 반환 (대문자로)
- INITCAP : 첫 글자를 대문자로 나머지는 소문자로 반환 (앞글자 대문자 나머지 소문자) 
    - SELECT LOWER('DATA manipulcation Language') AS "LOWER", UPPER('DATA manipulcation Language') AS "UPPER", INITCAP('DATA manipulation Language') AS "INITCAP" FROM DUAL;
    - =>Lower : data manipulcation language
    - =>Upper : DATA MANIPULCATION LANGUAGE
    - =>Initcap : Data Manipulation Language
- LPAD, RPAD (C1, n, C2) : 지정된 길이 n에서 C1을 채우고 남은 공간을 C2로 채워서 반환(L-Left, R-Right) (왼쪽이나 오른쪽 공간 채움)
    - SELECT LPAD('Java',10,'*') "LPAD", RPAD('Java',12,'^') "RPAD" FROM    DUAL;
     - =>LPAD : ******Java
     - =>Rpad : Java^^^^^^^^
- LTRIM, RTRIM(C1,C2) : LTRIM은 좌측 RTRIM은 우측의 공백문자를 제거, C2문자가 있는 경우 일치하는 문자를 제거 (제거)
- TRIM : 공백을 제거
    - TRIM(LEADING 'a' FROM '..') -> 앞의 문자와 공백 제거
    - BOTH : 양쪽 제거
    - FROM 만 적으면 기본값 BOTH
    - TRAILING : 뒤의 문자 제거
- SUBSTR(C,M,N) : 문자열의 일부분을 선택, M - 시작점(음수면 뒤에서부터), N - 선택할 길이(생략시 끝까지), C - 글자수  (전체에서 원하는 부분 출력)
    - SELECT  MEM_ID 회원ID,MEM_NAME 회원명,SUBSTR(MEM_NAME,1,1) 성 FROM MEMBER; => 회원이름과 성만 출력
    - SELECT  PROD_ID 상품ID,PROD_NAME 상품명 FROM PROD WHERE  SUBSTR(PROD_NAME, 4,2) = '칼라'; => 상품테이블의 상품명의 4번째 자리 부터 2글자가 '칼라' 인 상품의 코드와 상품명 출력
- REPLACE(C1, C2, C3) : 문자나 문자열을 지환, C1에 포함된 C2문자를 C3값으로 치환, C3없으면 찾은문자를 제거 (원하는 문자로 바꿈)
    - SELECT REPLACE ('SQL project', 'SQL') 문자치환1 FROM DUAL;
- INSTR (C1, C2, M, N) : C1문자열에서 C2문자가 처음 나타내는 위치를 리턴, M은 시작위치(생략시 1), N은 N번째 (위치 리턴)
    - SELECT  INSTR('hello heidi', 'he') RESULT1
- LENGTH, LENGTHB : 문자열의 길이를 출력, B는 byte 출력(한글은 3바이트) (길이구하기)


### 숫자열 함수
- ABS(n) : n의 절댓값
- SIGN(n) : n이 양수 음수 0 구분, 1 -1 0 리턴
- POWER(n,Y) : 승수 값(n의 Y승)
- SQRT(n) : n의 제곱근
- GREATEST(m, n , ...) : 열거된 항목 중 가장 큰 값 리턴
- LEAST (m, n, ...) : 열거된 항목 중 가장 작은 값 리턴
- ROUND(n,I) : 지정된 자릿수(I) 밑에서 반올림
- TRUNC(n,I) : ROUND와 동일 단, 반올림 아닌 절삭
- MOD(c, n) : n으로 나눈 나머지(c % n)
- FLOOR(n) : n과 같거나 작은 수 중에 가장 큰 정수(내림)
- CEIL(n) : n과 같거나 큰 수 중에 가장 작은 정수, 소수점 이하의 값이 존재하면 무조건 올림(올림)

### 날짜열 함수
- SYSDATE : 시스템에서 제공하는 현재 날짜와 시간 값
    - SYSDATE +- 1 => 하루 전후
    - SYSDATE +- 1/24 => 1시간 전후
    - 일반 문자형을 날짜형으로 -> TO_DATE(문자)
    - 현재 날짜와 특정 날짜를 연산시 일수가 계산