
## JPA란 뭘까요?

자바 객체 영속성을 위해
객체지향과 관계형 데이터베이스 사이를 매핑하는 다리 역할을 해주는 자바 ORM 표준 인터페이스입니다.  
JPA는 명세일 뿐이지 실제 동작을 하지는 않습니다. 구현체가 필요한 것이죠.
대표적인 구현체로는 `hibernate`가 있습니다.

## ORM 이 뭔데요?
객체 관계 매핑이라는 뜻으로, 객체 지향언어는 객체답게 구현 하고 데이터베이스는 관계형으로 구현하면
이 사이에 패러다임의 불일치가 생기는데, 이 두개의 불일치를 대신 해소해주는 역할을 하는게 ORM 프레임워크입니다.

## JPA 등장의 배경

자바는 객체지향언어다. 디비 세계의 메인스트림은 RDB이다.  
결국은 우린 SQL 중심 개발을 한다.  
만약 멤버테이블의 새로운 필드를 만들면, CRUD 쿼리도 필드를 반영해줘야하고, BO객체에도 필드를 추가해줘야 한다.   

**→ SQL 의존 개발을 하게된다**  

**객체답게 모델링하도록 매핑 작업만 늘어난다.** (OOP 를 지킬수록 미스매치만 많이 일어난다)  
객체를 자바 컬렉션에 저장하듯이 디비에 저장할 수는 없을까에 대한 대답이 JPA 다.

## JPA 는 왜쓰는거같아요?

1. 과거는 객체를 db 에 저장하려면 sql, JDBC API 직접 작성
2. JDBC Template, MyBatis 같은 매퍼가 생겨서 조금 편해짐. SQL은 직접써야한다
3. JPA는 SQL 조차 작성필요없음

### JPA 를 왜써야하는가 요약

- SQL  중심 → **객체 중심 개발로 변할 수 있다**
- **생산성** - CRUD 인터페이스가 이미 정해져있음 (수정: member.setName(”choi”) )
- **유지보수** - 필드 추가되어도 쿼리수정 필요없음. SQL은 만들어주니까. 객체 필드만 추가하면 됨
- **패러다임** 불일치 해결

### 동작위치

JAVA APP → JPA → JDBC → RDB


## N+1 문제에 대해 설명해봐라
N+1문제라는 것은, 개발자는 1개의 쿼리만이 수행될거라 기대했는데 N개 만큼의 쿼리가 추가로 호출되는 경우입니다. 
예를 들어, 다대일 관계에서 (고양이 -> 주인) 주인을 findAll했는데 각 주인 row별로 고양이를 조회하는 쿼리가 실행이 된다는 것입니다.  

- 해결법
1.Join Fetch를 이용한다.
`@Query("select DISTINCT a from owner a join fetch a.owner_id cat s join fetch s.onwer_id")`
2. Entity Graph 를 이용한다.
```java
@EntityGraph(attributePaths = {"cats", "cats.owner_id"})
@Query("select DISTINCT a from onwer a")
List<Academy> findAllOwner();
```

## 영속성 컨텍스트에 대해 설명해주세요

## transaction의 propagation 설정에 관해

