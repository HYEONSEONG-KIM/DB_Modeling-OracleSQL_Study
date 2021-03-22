# Subquery
- SQL 구문 안에  또 다른 Select  구문이 있는 것을 말함
- Subquery 가 없다면 SQL구문은 너무 많은 Join을 해야 하거나 구문이 복잡해짐
- Subquery 는 괄호로 묶음
- 연산자와 사용할 경우 오른쪽에 배치
- FROM 절에 사용하는 경우 View와 같이 독립된 테이블처럼 활용되어 inline view 라고 함
- Main query 와 Sub query 사이의 참조성 여부에 따라 연관(Correlated) 또는 비연관 (Noncorrelated) 서브쿼리로 구분
- 반환하는 행의 수, 컬럼수에 따라 단일행/다중행, 단일컬럼/다중컬럼 으로 구분하며 대체적으로 연산자의 특성을 이해하면 쉬움
- MAIN QUERY가 실행되기 전에 한 번 실행
- DML문과 CREATE TABLE 또는 VIEW에서 사용
- 알려지지 않은 조건에 근거한 값들을 검색하는 SELECT 문장을 작성하는데 유용
- 상관관계  서브쿼리(Correlated Subqueries) : 바깥쪽 쿼리의 컬럼 중의 하나가 안쪽 서브쿼리의 조건에 이용되고, 그 결과는 다시 바깥쪽 쿼리에 영향을 주는 처리 방식



## 위치에 따른 명칭
- SELECT문에 있는 쿼리 : SCALAR
- FROM 문에 있는 쿼리 : INLINE VIEW
- WHRER 절에 있는 쿼리 : NESTED



## 행과 열에 따른 SUBQUERY
- 단일 행(Sing-Row) 서브쿼리 : SELECT문장으로부터 오직 하나의 행만을 검색하는 질의
    - 단일 행 연산자(=,>, >=, <, <=, <>, !=) 
- 다중 행(Multiple-Row) 서브쿼리 : SELECT문장으로부터 하나 이상의 행을 검색하는 질의
    - 다중 행 연산자(IN, NOT IN, ANY, ALL, EXISTS)
        - ANY : OR의 의미
        - ALL : AND의 이미
 - 다중 열(Multiple-Column) 서브쿼리 : SELECT문장으로부터 하나 이상의 컬럼을 검색하는 질의
- FROM절상의 서브쿼리(INLINE VIEW) : FROM절상에 오는 서브쿼리로 VIEW처럼 작용
 - 상관관계 서브 쿼리 : 바깥쪽 쿼리의 컬럼 중의 하나가 안쪽 서브쿼리의 조건에 이용되는 처리 방식

## SET(집합)
- 조건
    - 컬럼의 개수가 동일
    - 대응되는 컬럼의 자료형이 동일
    - 처음 select 구문에 적용된 컬럼의 타입, 개수, 이름이 기준
    - CLOB, BLOB, BFILE, VARRAY 타입은 사용불가
    - ORDER BY절 마지막에 기술
- UNION : A집합과 B집합의 합집합
    - A UNION B : 모든자료 조회, 중복제거
    - A UNION ALL B : 모든자료 조회
- INTERSECT : A집합과 B집합의 교집합
- MINUS : A집힙과 B집합의 차집합


## EXISTS
- A집합과 B집합 사이에 AND EXISTS 
- B집합을 괄호로 묶은 후 B집합에 조인조건을 쓰면 됨
- 교집합과 다른 점은 컬럼의 개수가 달라고 사용 가능(집합에서는 사용 불가였던 조건인 가능)
- NOT을 붙이면 차집합