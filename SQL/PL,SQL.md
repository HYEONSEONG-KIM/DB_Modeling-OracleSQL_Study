# PL/SQL

## PL/SQL 이란?
- PL/SQL은 Procedural Language/SQL
- 서버에서 절차적인 처리를 위해 표준 SQL을 확장한 절차적 언어
- 블록(block) 구조로 여러 SQL문을 한번에 실행
- 모듈화, 캡슐화가 가능
- 변수, 비교, 반복, 예외처리 가능
- 서버에 저장되어 빠르게 실행됨

## 기능
- Anonymous block : 단순 스크립트에서 실행되는 블록 서버에 저장되지 않음
- Stored Procedure : 자주 실행되거나, 복잡한 비즈니스 로직을 미리 작성하여 서버에 저장하여 사용
- User Function : Procedure와 유사하며, 실행결과를 반환한다.
- Package : 여러 Procedure, Function 및 변수 등을 하나로 묶음
- Trigger : 테이블이나 뷰에 INSERT, UPDATE, DELETE등이 수행 전 또는 수행 후 자동 실행되는 Procedure
- 뻐스타 => PUSTA

## 확장 요소
- DECLARE : 지역변수와 커서, 사용자 예외를 선언
- := , SELECT  INTO , FETCH  INTO : 변수할당
- BEGIN…END	: 문장의 블록
- -- , /*…*/ : 한라인 주석 , 여러 라인 주석
- IF…ELSIF…END IF , CASE…END CASE : 분기문
- WHILE…END LOOP , LOOP…END LOOP , FOR…END LOOP : 반복문
- EXIT : 반복 블록을 빠져나간다
- GOTO : 처리 순서 변경하기
