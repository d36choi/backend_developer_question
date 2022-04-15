# Spring 을 왜쓰는가? (장점)

- 엔터프라이즈 수준의 개발을 진행하는데 필요한 기능을 경량화하여 제공합니다
- 객체들의 라이프사이클을 IoC컨테이너가 대신 관리해줍니다
- 웹개발이나 API개발에 필요한 MVC프레임웤을 제공합니다
- JDBC 운영을 위해 필요한 공통적인 코드를 대신 만들어주고 설정도 용이합니다
- API 예외처리가 용이합니다

# Spring 의 하위 컴포넌트들 아는 것들 이야기해보세요

- Core : IoC,DI 컨테이너를 포함한 근본적인 모듈
- JDBC : 매번 프로젝트 생성시마다 반복되는 JDBC 설정을 대신해주는 추상화 계층 활성화
- ORM integration : JPA, Hibernate 같은 객체관계매핑 API 의 통합 레이어를 제공
- Web : Servlet listener, web기반 application context 기능을 제공
- MVC framework : Model View Controller 패턴의 웹 모듈
- AOP : 관점지향형 설계 구현이 가능한 interceptor, pointcut 제공

# 의존성주입 DI 가 뭡니까?

객체를 주입하는 주체가 내가 아니라 컨테이너에게 있는 것입니다. 이 관점을 IoC(Inversion of Control) 이라 합니다.
스프링 IoC 컨테이너는 우리가 주입되어야할 객체를 추상화만 하면 실제 주입을 대신 해줍니다.

## Bean 이 뭔데요?

IoC 컨테이너가 관리하는 자바 Object 이고요. 기본적으로 Singleton scope 로 초기화됩니다.

## Bean Scope 에 대해 설명해주시죠

- singleton
- prototype
- Request
- session
- Global-session


# 의존성 주입 방법 뭐있어요?

생성자주입, 필드주입, 세터주입

### 이중에서 뭐가 권장되나요?

생성자주입입니다.   
순환참조가 발생하지 않습니다.    
객체 생성 시점에 해당 오브젝트들이 객체에 주입되는 것을 보장할 수 있습니다.  
setter, field 주입은 그렇지않고도 객체를 생성할 수 있습니다. 주입되는 타이밍도 개발자에 따라 달라질 수 있습니다.  
또한 생성자주입만이 `final`키워드로 초기화 할 수 있습니다.

# BeanFactory, ApplicationContext 의 차이?

BeanFactory는 Bean 인스턴스 관리 및 생성하는 컨테이너의 인터페이스  
AC는 스프링 컨테이너의 모든 정보, metadata 와 bean 을 포함한 인터페이스입니다.  
[정보](https://docs.spring.io/spring/docs/current/spring-framework-reference/html/beans.html)

# Singleton Bean 은 Thread-safe 한지?

아뇨. 싱글턴패턴은 생성에 관한 개발패턴이지, 실행에 대한 패턴이 아닙니다.
스레드 안전 여부는 bean 자체에 달려있습니다.

## Bean 생성 주기에 대해
http://www.dineshonjava.com/2012/07/bean-lifecycle-and-callbacks.html

## Spring MVC Request Life Cycle


## filter 와 interceptor 의 설명
- filter : DispatcherServlet 이전에 request 가 거쳐갑니다. 로그인 세션이나 PC Mobile 분기, XSS 등을 처리 합니다.
- interceptor : ApplicatonContext 내부에서 동작합니다. (filter는 밖) 따라서 빈으로 등록 가능합니다. 
controller method 호출 전후, view resolve 전에 끼어들어 처리할 수 있습니다.  

[spring-interview](https://www.baeldung.com/spring-interview-questions)
[filter interceptor aop](https://goddaehee.tistory.com/154)
