# SQL이란?
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

### CRUD
- C : CREAT (INSERT)
- R : READ (SELECT)
- U : UPDATE(UPDATE)
- D : DELETE(DELETE)
