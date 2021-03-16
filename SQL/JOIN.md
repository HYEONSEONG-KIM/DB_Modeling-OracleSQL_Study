
# Tabel Join 
- RDB의 핵심, 관계형 DB의 가장 큰 장점은 많은 TABLE을 JOIN하여 원하는 결과를 도출
- Join시 두 테이블간의 공통점이 있어야 함(관계가 있어야 함)
- Cartesian Product : 모든 가능한 행들의 조합
    - 관계있는 테이블끼리 묶어주기만 하면 됨
- Equi Join : 조건이 일치하는 컬럼을 매칭(주로 PK와 FK), (Simple Join) = 내부조인(Inner Join)
    - WHERE절에 두 테이블의 기본키, 외래키 값을 이용하여 조건
- Outer Join : 조건이 일치하더라도 모든 행들을 검색하고자 할 때 사용, +로 표시
    - FROM R.C = S.C(+) => LEFT OUTER JOIN
    - FROM R.C(+) = S.C => RIGHT OUTER JOIN

## ANSI 표준
- ANSI 표준으로 작성된 SQL은 모든 데이터베이스에서 호환
- Cartesian Product의 표준 => CROSS JOIN
    - FROM A CROSS JOIN B 
- Equi Join 의 표준 => INNER JOIN ()ON (조건)
    - FROM A INNER JOIN B ON(조건)
- Outer Join 사용시 LEFT, RIGHT 구분
    - FROM A LEFT(RIGHT) OUTER JOIN B(조건)
    - FROM A FULL JOIN B ON(조건) => 둘다
    - OUTER JOIN에 조건(날짜, 특정ID 등등)은 ON 안에 넣어야 함