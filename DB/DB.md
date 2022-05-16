

## DBMS가 SQL 의 조인 순서를 결정하는 방식에 대해 설명하시오

https://devuna.tistory.com/36

https://itstory07.tistory.com/714


## Primary key 와 candidate key 차이

- Candidate key는 각 레코드가 유일하게 식별될 수 있는 속성들의 집합입니다
- **유일성과 최소성이 만족되어야 합니다**
- Candidate key 중에 선발된 것이 PK 가 됩니다
- PK 는 객체의 튜플을 식별할 수 있는 유일 속성

## Primary Key 는 여러개가 될 수 있는가?
**PK 는 여러개가 될 수 없다. 그러나 PK 에 해당하는 칼럼은 여러개가 될 수 있다.**
무결성 제약조건을 위배하지 않기 위해 PK 의 칼럼은 여러개로 구성될 수 있습니다.
즉 (ID,NAME) 이 PK 면 ID=11, NAME=Kim 과 ID=11, NAME=CHOI 는 같이 존재할 수 있습니다.
그러나 PK 가 여러개일 수는 없습니다.

## PK 와 UNIQUE 제약조건의 차이
- PK 와 UNIQUE 조건 모두 특정 열에 고유성을 강제함 (해당 레코드가 유일하도록)
- 그러나 PK 와 다르게 UNIQUE 는 NULL 이 허용됩니다
- 물론 NULL 값도 고유성을 가져야해서 한 레코드만 허용됩니다
- UNIQUE 가 위배되면 SQLConstraintViolationException 이 발생합니다
