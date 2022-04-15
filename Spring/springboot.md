## Spring vs Spring Boot 의 차이는 무엇인가?
- Spring 의 보일러플레이트 코드를 작성하지 않도록 해준다.
- Auto Configuration을 지원한다.
  - 예를 들어 스프링에선 JDBCTemplate 생성해 빈등록해서 디비 설정해야했지만 부트는 그렇지 않다.
- POM starter를 제공합니다.
  - 우리는 그래서 web starter를 쓰면 jackson-databind, tomcat 의존성들을 직접 추가할 필요가 없습니다.
- spring actuator 를 제공합니다.
  - 이를 통해 위험감지가 가능합니다.  

https://sas-study.tistory.com/299  
https://incheol-jung.gitbook.io/docs/q-and-a/spring/spring-boot  
