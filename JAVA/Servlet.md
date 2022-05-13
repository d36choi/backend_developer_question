## Servlet 과 JSP 의 특성과 차이점?
### Servlet
**웹서버 동작을 위해 필요한 기능이 표준화되어있는 Java program**  
Java 코드 내에 HTML 이 포함된 형태. WAS 에 의해 요청에 맞는 서블릿이 호출이 됩니다.  

### JSP
Java Server Page 의 약자.
Java 기반의 서버 스크립트 언어입니다.
기존 서블릿에서는 뷰를 구성할때, 자바코드로 복잡하게 작성해야하지만  
JSP 로 작성하면 **HTML 에 JAVA 코드가 포함된 형태** 로 개발이 가능해 훨씬 편리합니다.  
WAS 에 의해서 서블릿(.java) 파일로 컴파일이 되게 됩니다.  
그래서 Servlet 기능들 (request, response, session, cookie)을 그대로 사용가능하고 
JSTL, EL 등을 통해 더 편리하게 뷰를 개발할 수 있습니다.  



[JSP , Servlet](https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html)
