> 스프링을 이해하는데는 POJO를 기반으로 한 삼각형 그림을 이해하여야 한다. 삼각형은 3대 프로그래밍 모델에 대한 이야기다.


# IoC/DI
`Inversion of Control` `Dependency Injection`  

# AOP
`Aspect Oriented Programming`  
DI가 의존성의 주입이면 이것은 로직의 주입이다.  
여러 기능을 나열할 때, 어느 순간에 구현되어야하는 공통의 기능들이 있을 것이다.  
이를 **횡단 관심사(CROSS-CUTTING CONCERN)** 라고 한다.
이런 중복된 횡단 관심사는 분리하여 관리할 수 있다.  
이를 목표로 하는 것이 AOP 이고 스프링은 메서드 시작 전, 메서드 전체, 메서드 종료, 정상 종료, 예외발생 종료
이 5군데에 횡단관심사의 주입이 가능하다.

# PSA
`Portable Service Abstraction`   
일관성 있는 서비스 추상화다.
예로는 JDBC가 있다. 우리는 연결하려는 DB 종류가 무엇이든, Connection, Statement, Resultset을 사용하면
똑같은 코드로 똑같은 목적을 이룰 수 잇다. 데이터베이스 종류가 달라도 어댑터 패턴을 통해  
같은 일을 하는 다수 기술을 하나의 공통 인터페이스로 제어할 수 있는 것이다.
스프링 프레임워크 안에서도 이 서비스 추상화를 통해 다양한 기능을 제공한다.  
이처럼, 서비스 추상화를 해주면서 일관성있는 방식을 제공한다고 해서 PSA라고 한다.  
ORM, Cache, Transaction 등 다양한 PSA를 제공한다.

# 응집성과 결합성



[스프링 입문을 위한 자바 객체 지향의 원리와 이해](http://www.yes24.com/Product/Goods/17350624)
