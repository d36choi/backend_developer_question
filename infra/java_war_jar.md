## JAR, WAR 차이점?

### JAR

java archive. 자바프로그램 압축파일이라고 난 생각한다. 클래스,라이브러리, 리소스, 설정파일을 압축해 만들어진 애플리케이션 혹은 **라이브러리**다.  
JRE만 있으면 실행가능하다.


### WAR

WEb Application Archive. **웹 어플리케이션** 실행을 위한 압축 설정 파일이다.  
JSP , servlet 등 WAS 컨테이너를 통해 동작할 수 있다. **WEB-INF/lib, web.xml** 을 포함한다.  
web.xml 에서는 path 설정을 통해 서버에서 필요한 정적리소스의 위치를 알 수 있게 해준다.  
Tomcat, WebLogic 등 외부 WAS가 있어야만 동작이 가능하다.  

```
META-INF/
    MANIFEST.MF
WEB-INF/
    web.xml
    jsp/
        helloWorld.jsp
    classes/
        static/
        templates/
        application.properties
    lib/
        // *.jar files as libs
```
* The META-INF/MANIFEST.MF는 아카이브에 포함된 파일들의 메타데이터를 가지고 있다.


### 사용 목적의 차이가 중요하다
가장 큰 차이는 JAR 는 어플리케이션, 라이브러리로써 쓸 수 있고, WAS는 웹 어플리케이션으로만 가능하다

### Springboot 가 JAR를 쓰는 이유?
내장형 톰캣이 JAR 파일에 포함이 되어있기 때문입니다.

[jar,war](https://www.baeldung.com/java-jar-war-packaging)
