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

## URI , URL 의 차이는 무엇인가요 ?
Unifrom Resource Identifier 와 Location.  
URI > URL 을 포함하는 개념입니다. 차이는 자원의 위치를 명시하느냐 자원의 식별까지 명시하느냐의 차이입니다.  
`scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]`  
XXX.com/index.html 에서 queryString 까지 명시가 된다면 그건 URI 이고 URL이 아닙니다.  


## HTTP, TCP 의 차이 ?
두 개가 배타적인 관계라고 하기는 어렵습니다.  
계층이 응용계층인 규약과 transport 계층이기 때문이고요. HTTP는 TCP 를 거쳐 통신합니다.  
HTTP는 stateless 한데 (즉 각 요청이 독립적. 서로 영향없음) TCP는 3way handshake를 통한 연결지향형 통신입니다.  
다만 HTTP는 요청과 응답이 이루어지면 TCP 연결을 FIN 을 주며 끊어버리는 것입니다.  

## www.naver.com 에 접속할 때 인터넷 세상에 일어나는 일의 과정 ?
- 브라우저가 uri를 확인
- http일 경우 해당 도메인 캐싱 되어 있는지 확인
- DHCP서버에서 사용자 자신의 IP주소, 가장 가까운 라우터의 IP주소, 가장 가까운 DNS서버의 IP주소
- ARP 통해서 가까운 라우터 주소 확인
- DNS 통해 IP주소 식별
- TCP 통해 3way handshake 후 소켓 개방 및 연결

