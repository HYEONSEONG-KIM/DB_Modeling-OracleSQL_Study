# SQL문법

## Datatpye(크기)
- 숫자 : NUMBER(자릿수,max 38자리)
- 고정길이 문자 : CHAR(max 2000byte) -> Update시 편이
- 가변길이 문자 : VARCHAR2(한글 1글자 - 3btye,max 4000byte) -> Update시 불편
    + 남은 공간을 어떤식으로 처리하느냐에 따라 달라짐(char는 공백이 남아있고, varchar는 공백을 반납)
- 날짜 : DATE
- 빈 공간을 허용 하지 않으면 N.N(Not Null) - Mandatory(필수)
- 빈 공간을 허용 하면 아무것도 기입하지 않음 - Optional(선택)

## Select
- 선택 및 조회
- SELECT *FROM ALL_USERS; -> 모든 유저 조회

## create
- 생성, 만들다
- CREATE USER TEST IDENTIFIED BY java:
    + TEST라는 계정을 java라는 비밀번호로 생성
    + IDENTIFIED BY -> 비밀번호 설정

## Drop
- 계정 삭제
- DROP USER (계정명) CASCADE;