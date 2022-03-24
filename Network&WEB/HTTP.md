## CORS란 무엇인가 ?

Cross-Origin-Resource-Sharing. 교차 출처 자원 공유이다.
SOP(Same Origin Policy) 를 위배하는 요청에 대해서 허용할지 말지를 정하는 HTTP 정책이다.  
여기서 origin 은 protocol, domain, port 세 개의 합을 뜻한다.  
|프로토콜|도메인|포트|
|------|---|---|
|https://|d36choi.com|:8080|

Access-Control-Allow-Origin 헤더를 응답에 포함시키는 것으로 허용 가능하다.  

이 정책이 있는 이유는 서로다른 출처의 요청이 제한되지 않으면 보안 상 이슈가 생길 수 있기 때문이다.

### CORS에서 preflight request란 무엇이며 어떤 경우에 발생하는가 ?
요청을 보내기 전, 서버에게 CORS 를 허용하는지를 확인하는 선행 단계이다. OPTION 메서드로 보낸다.  

서버는 허용하는 오리진인 경우에 허용하는 메서드들을 200OK 와 함께 알려준다.
