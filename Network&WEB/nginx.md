## Nginx 의 reverse Proxy 에 관해 설명하시오
리버스 프록시 서버는 외부로부터 오는 요청을 내부의 서버로 중계해주는 기능입니다. nginx 를 쓸 때 우리가 다루는 주된 기능입니다.
**장점**
- 내부 서버를 외부에 노출안해도 됨
- 로드밸런싱 가능
- CORS 해결 가능

**방법**
특정 path 에 대해 add header Access-Controll-Allow-Origin header 를 추가한다
