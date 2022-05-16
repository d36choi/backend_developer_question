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


## HTTPS 란?
보안이 약한 HTTP에 SSL / TLS 을 추가한 형태. 세션을 암호화한다. 사용자가 서버에 보내는 정보를 암호화합니다.  
따라서 중간자가 탈취해도 암호화된 데이터를 봅니다.  
제3자가 발급한 인증서를 이용해 클라이언트는 서버의 신뢰성을 확인할 수 있습니다.  
또한 데이터의 무결성이 보장됩니다.  

## HTTP status code 를 아는대로 말해보세요

**상태코드**
- 1XX 정보성 상태 코드
- 2XX 성공 상태 코드
- 3XX 리다이렉션 상태 코드
- 4XX 클라이언트 에러 상태 코드
  - 400 **Bad Request** 클라이언트가 잘못된 요청을 보냄
  - 401 **Unauthorized** 리소스를 얻기 전에 클라이언트에게 스스로를 인증하라고 요구
  - 403 **Forbidden** 요청이 서버에 의해 거부되었음 (보통 서버가 본문에 거절 이유를 보내고 명세하지 않으려 할 때 사용하는 코드)
  - 404 **Not Found** 서버가 요청한 URL을 찾을 수 없음 (본문에 클라이언트 어플리케이션이 사용자에게보여주기 위한 내용을 담을 수 있음 ex.404 를 나타내는 HTML 문서)
  - 405 **Method Not Allowed** 요청한 URL에 대해, 지원하지 않는 메소드로 요청받았을 때 사용
  - 406 **Not Acceptable** 주어진 URL에 대한 리소스 중 클라이언트가 받아들일 수 없는 경우 사용
  - 408 **Request Timeout** 클라이언트의 요청을 완수하기에 시간이 너무 많이 걸리기 때문에, 해당 코드로 응답하고 연결을 끊음
- 5XX 서버 에러 상태 코드
  - 500 **Internal Server Error** 서버가 요청을 처리할 수 없게 만드는 에러를 만났을 때 사용
  - 502 **Bad Gateway** 프락시나 게이트웨이처럼 행동하는 서버가 연쇄작용 할 링크로부터 가짜 응답에 맞닥뜨렸을 때 사용
  - 504 **Gateway Ttimeout** 다른 서버에 요청을 보내고 응답을 기다리다가 타임아웃이 발생한 게이터웨이나 프락시에서 온 응답

[상태코드 [작심삼일]](https://dev-junior.tistory.com/7)
