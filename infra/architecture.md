## Layered Architecture 에 관해 설명해보세요
개발자간에 정해놓은 로직별 계층화 패턴입니다. 각 계층은 각자의 역할에만 관심사를 가집니다.  
이를 통해, 우린 이 아키텍처를 정해놓으면 개발할 때 유지보수가 쉬워지고 재사용성이 나아질 수 있습니다.  

- presentation layer : 사용자 요청을 제일 먼저 받는 계층. 데이터 변조를 담당. `Controller`.  
cilent로부터 request를 받고 response를 return하는 api 정의.  
api route별 로깅, 보안 등의 전처리.  
  
- Business layer : 비즈니스 로직이 수행되는 계층, `Service` 컴포넌트에 해당. 
- Persistance layer : 영속성 계층. 비즈니스 로직을 통해 만들어진 객체들을 DB에 접근해 CRUD 를 수행하는 역할 `Repository`
- Database layer : 영속화된 객체들이 저장되는 공간(DB)




### link

- [with gradle](https://medium.com/riiid-teamblog-kr/gradle%EA%B3%BC-%ED%95%A8%EA%BB%98%ED%95%98%EB%8A%94-backend-layered-architecture-97117b344ba8)
- [oreily](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html)
