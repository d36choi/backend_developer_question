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


## HTTP 1.1의 Keep-Alive 헤더는 어떤 의미인가 ?

HTTP 는 Connectionless 한 통신이다. 매 요청마다 3way handshake를 통해 비용문제가 발생하는 구조다.  
1.1부터 Keep-Alive 헤더가 기본설정되어 있다. 이 시간 동안에는 하위 레이어인 TCP 연결이 끊어지지 않고 유지된다.
`Keep-Alive: timeout=5, max=99`

- 장점: 연결이 유지된 시간동안 재요청이 올 때, 시간단축이 가능
- 단점: 연락이 안오더라도 모든 요청에 대해 연결을 각각 유지해야하기 때문에 다중 접속 상황에서 성능이 떨어짐


## HTTP 응답 헤더중 ETag는 어디에 사용되는가 ?
브라우저 캐시와 웹 서버 응답 파일의 컨텐츠 일치 여부를 판단한다.
ETag 가 다르면 브라우저는 캐시된 내용과 다른 정적 컨텐츠가 내려온걸로 판단해 캐시를 지우고 새 컨텐츠를 그려준다.  

