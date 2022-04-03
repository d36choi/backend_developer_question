## Apache vs Tomcat 을 설명해보시오

가장 큰 차이는 `Servlet`의 유무입니다.

아파치는 Web Server 입니다. 설정한대로, client 의 HTTP 요청에 대해 정적파일을 돌려주는 응답을 합니다.

톰캣은 Web Server 기능을 포함한 WAS(Web Application Server)에 가깝습니다. 우리가 스프링 부트 프로젝트를 시작하면 자동으로  
내장된 톰캣 서버가 구동되고 작성한 코드에 따라, HTTP 요청에 맞는 동적인 데이터와 정적파일들을 응답으로 보내줄 수 있습니다.  
내장된 `서블릿 컨테이너` 를 통해 요청별로 스레드를 생성해, 개발자가 서블릿 인터페이스에 맞게 개발한 코드를 동작시킵니다.  


## 우리가 두 개를 같이 쓰는 이유

매번 같은 응답을 해줘도 되는 요청의 경우에 매번 서블릿을 거치게 하는 건 낭비입니다.  
우리는 그런 요청에 대해서는 Web Server 인 아파치의 선에서 응답을 줄 수 있다면 효율적이기 때문입니다.  

그리고 로드밸런싱의 문제 또한 있습니다. WAS 를 여러개 구상하고 WS인 아파치를 통해 요청을 여러 WAS에 분산시킬 수 있다면  
대규모 트래픽에 견딜 수 있습니다.  
![image](https://user-images.githubusercontent.com/40600306/161429488-c0a7fc72-b60a-4213-8947-2de7c0c92c6e.png)



[WAS, WS](https://tecoble.techcourse.co.kr/post/2021-05-24-apache-tomcat/)
