# DDL
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

## INDEX
- 검색속도가 빨라지게 해주는 자료구조
- SELECT 할 때 인덱스를 생성시 설정했던 묶어놓은 속성들을 검색할때 사용

# DML
- INSERT : 데이어 삽입, INTO : 삽입될 테이블 지정
    - INSERT INTO <테이블명>(속성) VALUES(넣을 값들);
    - 데이터의 개수와 컬럼의 개수가 같은경우 컬럼 생략가능(되도록이면 컬럼도 함께 작성)
    - NULL값 입력
        - 속성을 비워두고 값 삽입시 위치에 대응되게 입력
        - 속성을 모두 적고 값 삽입에 NULL 혹은 ''(오라클에서만 NULL로 인식)
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
