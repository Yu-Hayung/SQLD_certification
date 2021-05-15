# 관계형 데이터 베이스 


![](https://images.velog.io/images/yuhayung7296/post/77609499-230c-41a1-a0c6-43ad642a2afd/image.png)

![](https://images.velog.io/images/yuhayung7296/post/05604510-e594-4a9f-bd71-7e0b3c14fca9/image.png)

![](https://images.velog.io/images/yuhayung7296/post/cbaf27ef-1e3d-4b43-8217-cf08e35fbb51/image.png)

## 문장들의 종류 

![](https://images.velog.io/images/yuhayung7296/post/b8ad7955-71c2-4d68-b121-5acbf536793c/image.png)

# DDL 

**CHARACTER**
: 고정 길이 문자열 정보
**VARCHAR**
: 가변길이 문자열 정보
**NUMERIC**
: 정수, 실수등 숫자 정보
**DATETIME**
: 날짜와 시각정보 

제약조건 
**CONSTRAINT**
: 사용자가 원하는 조건의 데이터만 유지하기 위한 방법
**종류 =**  `PRMARY KEY`, `UNIQUE KEY`, `NOTNULL`, `CHECK`, `FOREIGN KEY`, `NULL`, `DEFAULT`


# 테이블
## 테이블 생성의 주의
- 테이블명은 객체를 의미할 수 있는 적절한 이름을 사용한다. 
: 기능한 단수형을 권고한다. 
- 데이블 명은 다른 테이블의 이름과 중복되지 않아야 한다. 
- 한 테이블 내에서는 칼럼명이 중복되게 지정될 수 없다. 
- 데이블 이름을 지정하고 각 칼럼들은 괄로 '( )'로 묶어 지정한다.
- 각 칼럼들은 콤마 ','로 구분되고, 테이블 생성문의 끝은 항상 세미콜론 ','으로 끝난다. 
- 칼럼에 대해서는 다른 테이블까지 고려하여 데이터베이스 내에서는 일관성 있게 사용하는 것이 좋다. 
- 칼럼 뒤에 데이터 유형은 꼭 지정되어야 한다.
- 테이블명과 칼럼명은 반드시 문자로 시작해야 하고, 벤더에서 사전에 정의한 예약서는 쓸 수 없다. 

## 테이블 구조
- 칼럼과 행의 2차원 구조를 가진다.
- 데이터를 저장하는 객체로서, 데이터 모델 상의 엔터티를 관계형 데이터 베이스에서 물리적으로 구현한다. 
- 칼럼은 테이블의 세로 구조에 해당하며, 데이터 모델 상의 속성과 매칭된다. 

## 테이블내 칼럼 삭제 
- **ALTER TABLE **
테이블 명 
**DROP COLUMN**
삭제할 칼럼명; 

✔️ DROP COLUMN : 모두 삭제가능, 한번에 하나의 칼럼만 삭제 가능

✔️ DROP CONSTRAINT : 테이블 생성시 부여했던 제약조건을 삭제

✔️ ADD CONSTRAINT :테이블 생성 이후에 필요에 의해서 제약조건을 추가 

✔️ DROP COLUML : 테이블 삭제   ➡️  복구 안됨, 참조되는 제약 조건도 삭제 


** TRUNCATE TABLE **
: 테이블 자체가 삭제가 되는 것이 아니고, 해당 테이블에 들어 있던 모든 행들이 제거되고 저장공간을 재사용 가능하도록 해제 한다. 
테이블 구조를 완전히 삭제를 하기 위해서는 DROP TABLE을 실생하면 된다. 

### 삭제 정리 

- **DROP** / DDL / Rollback 불가능 / Auto Commit / 
테이블의 정의 자체를 완전 삭제 
- **TRUNCATE** / DDL / Rollback 불가능 / Auto Commit / 
테이블을 최초 생성된 초기화 상태 만듬 
- **DELETE** / DML / commit 이전 Rollback 가능 / 사용자 Commit / 
데이터만 삭제 


## 테이블내 칼럼명 변경

- **RENAME TABLE**
**ALTER TABLE**
데이블 명
**RENAME COLUMN **
변경해야할 칼럼명
**TO** 새로운 칼럼명 ;

## 테이블에 데이터 입력

**INSERT INTO **
테이블명
**VALUES**
테이블에 넣을 값


## 입력된 데이터 수정

**UPDATE **
테이블명
**SET **
수정되어야할 칼럼명 = 수정되기를 원하는 새로운 값

## 데이터 조회 
**SELECT [ALL / DISTINCT] **
보고 싶은 칼럼명, ...
**FROM**
해당 칼럼들이 있는 테이블명 


✔️ `ALL` : 옵션이므로 별도로 표시하지 않아도 된다. (중복 출력)

✔️ `DISTINCT` : 중복된 데이터 1건으로 처리 출력.



# 트랜잭션의 특성 
- **원자성_atomicity**
트랜잭션에서 정의된 연산들은 모두 성공적으로 실행되지 아니면 전혀 실행되지 않은 상태로 남아 있어야 한다. 
- **일관성_consistency**
트랜잭션이 실행되기 전의 데이터베이스 내용이 잘못 되어 있지 않다면 트랜잭션이 실행된 이후에도 데이터베이스의 내용에 잘못이 있으면 안된다. 
- **고립성_isolation**
트랜잭션이 실행되는 도중에 다른 트랜잭션의 영향을 받아 잘못된 결과를 만들어서는 안 된다.
- ** 지속성_durability **
트랜잭션이 성공적으로 수행되면 그 트랜잭션이 갱신한 데이터베이스의 내용은 영구적으로 저장된다.

# TCL 
: Transation Control Language
## COMMIT, ROLLBACK
테이블 내 입력한 데이터나, 수정한 데이터, 삭제한 데이터에 대하여 **COMMIT** 이전에는 변경 사항을 취소할 수 있는데 
데이터베이스에서는 **롤백(ROLLBACK)** 기능을 사용한다. 

**롤백(ROLLBACK)**
데이터 변경 사항이 취소되어 데이터의 이전 상태로 복수되며, 관련된 행에 대한 장금 (LOCKING)이 풀리고 다른 사용자들이 데이터를 변경할 수 있게 된다. 

**정리**
**Transaction** 은 데이터베이스의 논리적 연산단위로서 밀접히 관련되어 분리될 수 없는 한개 이상의 데이터베이스 조작을 가리킨다.
**Transaction**의 종료를 위한 대표적 명령어로서는 데이터에 대한 변경 사항을 데이터베이스에 영구적으로 반영하는 **COMMIT** 과 데이터에 대한 변경사항을 모두 폐기하고 변경정의 상태로 되돌리는 **ROLLBACK** 이 있다. 

## SAVEPOINT 저장점
정의하면 롤백(ROLLBACK)할 때 트랜잭션에 포함된 전체 작업을 롤백하는 것이 아니라 현 시점에서 SAVEPOINT 까지 트랜잭션의 일부만 롤백할 수 있다.

# WHERE절 
where 절은 from 절 다음에 위치하며, 조건식은 아래 내용으로 구성된다. 
- 칼럼 명
- 비교 연산자
- 문자, 숫자, 표현식
- 비교 칼럼명

## 연산자 종류
![](https://images.velog.io/images/yuhayung7296/post/5d70d495-6b5d-45dc-9b93-961758bdb64a/image.png)

## 연산자의 우선순위 
1. 괄호로 묶은 연산
2. 부정 연산자(NOT)
3. 비교 연산자
4. 논리 연산자중 AND, OR 의 순서로 처리 


## BETWEEN , IN 등..

- **BETWEEN** a **AND** b
: a 와 b 값 아이에 있으면 된다.
- **IN**
: 리스트에 있는 값 중에서 어느 하나라도 일치하면 된다.
- **LIKE '비교 문자열'**
: 비교문자열과 형태가 일치하면 된다. 
- **IS NULL**
: NULL 값인 경우



# 함수 
## 필수 암기 함수 

![](https://images.velog.io/images/yuhayung7296/post/3e48705b-fa99-4c42-9cdf-6849477d9690/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-13%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.24.21.png)

![](https://images.velog.io/images/yuhayung7296/post/0ebc252a-a524-46d2-8368-356faf8b6987/image.png)

<한글 윈도우 함수 정리 이미지 못 찾음 ㅠㅠ>


![](https://images.velog.io/images/yuhayung7296/post/988b474b-b807-41ea-a26d-5e06363a3df8/image.png)


## NULL 관련 함수 

![](https://images.velog.io/images/yuhayung7296/post/c3560194-b9e0-479c-ba00-33f2a0d4d371/image.png)

- **NVL (표현식1, 표현식2) **
: 표현식1의 결과값이 NULL이면 표현식2의 값을 출력한다.
- **NULLIF (표현식1, 표현식2) **
: 표현식1이 표현식2와 같으면 NULL을 같지 않으면 표현식1을 리턴한다.
- ** COALESCE (표현식1, 표현식2) **
: 임의의 개수 표현식에서 NULL이 아닌 최초의 표현식을 나타낸다. 

# Group By, Having 절
## GROUP BY 문장
**SELECT** [DISTINCT]
칼럼명 [ALIAS명]
**FROM** 테이블명
[WHERE 조건식]
[GROUP BY
 칼럼 이나 표현식]
[HAVING 그룹조건식];

## Group By, Having 절 특징
- GROUP BY 절을 통해 소그룹별 기준을 정한후, SELECT 절에 집계 함수를 하용한다. 
- 집계 함수의 통계 정보는 NULL 값을 가진 행을 제외하고 수행한다.
- GROUP BY 절에서는 SELECT 절과는 달리 ALIAS 명을 사용할 수 없다. 
- 집계 함수는 WHERE 절에 올 수 없다.
- WHERE 절은 전체 데이터를 GROUP으로 나누기 전에 행동을 미리 제거시킨다. 
- HAVING 절은 GROUP BY 절의 기준 항몽이나 소그룹의 집계 함수를 이용한 조건을 표시 할 수 있다. 
- GROUP BY 절에 의한 소그룹별로 만들어진 집계 데이터 중, HAVING 절에서 제한 조건을 만족하는 내용만 출력한다. 
- HAVING 절은 일반적으로 GROUP BY 절 뒤에 위치한다. 


# Order By 절 

- **ASC(Ascending) **
: 조회한 데이터를 오름차순으로 정렬한다. (기본값 생략가능)
- **DESC(Descending)**
: 조회한 데이터를 내림차순으로 정렬한다. 

## Order By 절 특징 
- 기본적으로 오름차순이다. 
- 숫자형 데이터 타입은 오름차순으로 정렬했을 경우 가장 작은 값 부터 출력한다.
- 날짜형 데이터 타입은 오름차순으로 정렬했을 경우 날짜 값이 가장 빠른 값이 먼저 출력된다. 

# 문장 실행 순서 
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY


---

조인(JOIN) 은 양이 너무 많아서 따로 업로딩 하려 한다. 
오늘은 여기 까지~!! 🔥🙌🏻

