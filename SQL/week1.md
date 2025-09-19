서브쿼리 : 하나의 SQL 문 안에 포함된 SELECT 문

EX) SELECT *

    FROM t1

    WHERE 
    column1 = (
      SELECT column1 FROM t2

    )

서브쿼리 특징

1. 서브쿼리 안에 서브 쿼리를 넣을 수도 있다. (깊은 중첩)

2. 반드시 괄호로 감싸져야한다

서브 쿼리 장점

1. 쿼리를 분리하여 각 부분 쉽게 파악 가능
2. 복잡한 join이나 union 대체 방법 제공

서브쿼리는 select문에서 허용되는 대부분 요소 포함 가능

<DISTINCT, GROUP BY, ORDER BY, LIMIT, JOIN, 인덱스 힌트, UNION, 함수, 주석,
TABLE , VALUES>

서브쿼리 사용가능한 외부 구문

1.select
2.insert
2.update
4.delete
5.set
5.do

<서브쿼리 형태>

1. 스칼라 서브쿼리 (scalat subqery)

<특징>

1.데이터 타입

2.길이

3.NULL 가능

-> 단순한 피연산자로 단일 컬럼 값이나 리터럴이 허용되는 모든 곳에서 사용 가능

ex) CREATE TABLE t1 (s1 INT, s2 CHAR(5) NOT NULL);
INSERT INTO t1 VALUES(100, 'abcde');
SELECT (SELECT s2 FROM t1);

--> 결과 'abcde'

<사용제한>

1.리터럴 값만 허용할 때

ex) LIMIT(정수 리터럴만 허용) ,LOAD DATA (문자열 리터럴 파일만 하용)

--> CREATE TABLE t1 (s1 INT);
INSERT INTO t1 VALUES (1);

CREATE TABLE t2 (s1 INT);
INSERT INTO t2 VALUES (2);

SELECT (SELECT s1 FROM t2) FROM t1;

결과가 2가 나옴 

SELECT (SELECT s1 FROM t2) FROM t1;
= SELECT 2 FROM t1;

<표현식 안에서의 서브쿼리 사용>

