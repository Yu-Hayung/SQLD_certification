**조인[JOIN]** 의 양이 너무 많아서 이것만 따로 정리했다. 
🤦🏻‍♀️👏🏻👏🏻👏🏻👏🏻👏🏻👏🏻

---

# JOIN 조인 
: 두 개 이상의 테이블 들을 연결 또는 결합하여 데이터를 출력하는 것을 JOIN이라고 하며, 일반적인 경우 행들은 PRIMARY KEY(PK)나 FOREIGN KEY(FK) 값의 연관에 의해 JOIN이 성립된다.
하지만 어떤 경우에는 이러한 PK, FK의 관계가 없어도 논리적인 값들의 연관만으로 JOIN이 성립 가능하다. 


![](https://images.velog.io/images/yuhayung7296/post/b7ae3702-ce74-4857-837e-8c1b3f1c6d3c/image.png)

![](https://images.velog.io/images/yuhayung7296/post/7349b12d-81c4-48e3-b048-c7d2a4a6cc96/image.png)


그림으로 설명을 끝내고 싶지만 
내가 자주 틀리는 문제 또는 설명이 부실한 부분을 추가로 넣겠다. 

---

# EQUI JOIN 문장
**SELECT **테이블1, 칼럼명, 테이블2, 칼러명, ...,
**FORM** 테이블1, 테이블2 ..,
**WHERE** 테이블1, 칼럼명1 **=** 테이블2, 칼러명 ;
**➡️ WHERE 절에 JOIN 조건을 넣는다. **

# INNER JOIN 
- JOIN 조건에서 동일한 값이 있는 행만 반환한다.
- CROSS JOIN, OUTER JOIN 과 같이 사용 못함
- USING 조건절, ON 조건절을 필수적으로 사용해야 한다. 

# NATURAL JOIN
- 두 테이블 간의 동일한 이름을 갖는 모든 칼럼들에 대해 EQUI(=) JOIN 을 수행한다.
- 추가로 USING 조건절, ON조건절, WHERE 조건절 에서 JOIN 조건을 정의 할 수 없다.
- ALIAS나 테이블명과 같은 접두사 붙일 수 없다. 

# USING 조건절 
- 같은 이름을 가진 칼럼들 중에서 원하는 칼럼에 대해서만 선택적으로 = JOIN 가능
- SQLserver 지원안함 
- JOIN 칼럼에 대해서 ALIAS나 테이블이름과 같은 접두사를 붙일 수 없다. 


# ON 조건절 
- 칼럼명이 다르더라도 JOIN 조건절을 사용할 수 있다.
- WHERE 검색 조건은 충돌 없이 사용할 수 있다.
- ON 조건절에서 사용된 괄호는 옵션사항 이다.
- ALIAS 나 테이블명과 같은 접두사를 사용해야 한다. 


# OUTER JOIN 
- JOIN 조건에서 동일한 값이 없는 행도(NULL 값도) 출력된다.
- USING 조건절이나 ON 조건절을 필수적으로 사용해야 한다.


# CROSS JOIN
- JOIN 조건이 없는 경우 생일 수 있는 모든 데이터 조합 
➡️ **카티션 곱**


---

🔥🔥🔥🔥🔥🔥🔥 퐈이어~~ 🔥🔥🔥🔥🔥🔥🔥🔥🔥
