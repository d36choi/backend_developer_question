## HTTP 응답 코드 중 4xx/5xx는 어떻게 다른가 ?

> A 4xx code indicates an error caused by the user, whereas 5xx codes tell the client that they did everything correctly and it’s the server itself who caused the problem.
> 

에러의 유발원인에 따라 다르다.

400 → user 의 잘못이므로 알려줘야함. 500 → 서버의 잘못이고 클라이언트는 옳게 요청보냈음.

## restful api 를 설명하라
rest 하게 잘 구성된 api 를 의미합니다. rest (Representational State Transfer) 하다는 것은  
URI에 자원을 명시하고 HTTP method로 행위를 정의해서 서버로부터 데이터를 받거나 서버측에 데이터를 반영시키도록 하는 걸 명시적으로 잘 구현했다는 것이라고 생각합니다.  
- HTTP 여야 함
- stateless 해야 함
- 보안, 로드밸런싱 등 서버 내부구조를 클라이언트는 모르게 계층화해야함
### HTTP to CRUD
- POST : Create
- GET : Read
- PUT,PATCH : Update
- DELETE : Delete

### put, patch 차이
- put : 존재하는 자원의 **전체**를 바꿉니다
- patch : 존재하는 자원의 **일부**만을 바꿉니다
put, patch를 쓰면 꼭 그렇게 되리라는 개념보다는 그렇게 규약을 설정하는 것이 이롭다는 것입니다.  
내부 로직은 개발자가 정하기 나름이지만은요.

### GET,POST 의 차이가 뭔거같냐?

1. **캐싱 가능 여부**
- get 은 캐싱 가능하지만 post는 아닙니다
2. **response body 존재여부**
- post 만이 body를 갖습니다. get은 uri 에 필요 자원을 명시해야합니다. 따라서 민감데이터는 명시하면 안됩니다.
- 또한 uri 길이 제한이 있기 때문에 get 또한 요청문의 길이제한이 있다고 봐야합니다.
3. **멱등성**

- get 은 언제나 동일한 결과를 보여줍니다. only read


## XML, JSON 의 특징을 말해보세요
### JSON (JS Object Notation)
- 읽기 쉬움
- 다양한 객체로 표현 가능 (리스트, 맵)
- 파싱 쉬움
- 인자 및 응답 데이터 형식 지정 어려움 (모호함)
- 메타데이터 표현하려면 데이터에 같이 작성해야함
### XML (eXtended Markup Language)
- 읽기 어려움 (많은 줄 수와 인덴트)
- 파싱 어려움
- 값의 형식과 항목의 구조에 대한 명확한 정의가 가능
- 메타데이터 많이 표현되어있음
- 그러나 데이터 **형식적 무결성 보장 가능 장점**


https://sujl95.tistory.com/59


## Gateway 와 Proxy 의 차이

### 프록시
프록시는 클라이언트 - 서버 사이에 놓여 중개자 역할을 담당합니다.  
클라이언트는 프록시의 IP 주소만을 알고 요청을 보내기에 실제로 요청을 수행해야하는 목적지 서버의 정보는 숨겨집니다. (보안상 이점)
캐싱이 되기때문에 같은 요청에 대해서는 서버까지 가지않고 바로 캐싱된 데이터를 전달할 수도 있습니다. (캐시 프록시)
- 리버스 프록시
    - 서버 측에 프록시가 걸려있다. 인터넷세상에서 온 요청을 프록시가 먼저 받고 서버에게 요청을 중개한다.
- 포워드 프록시
    - 클라이언트 쪽에 프록시가 존재한다. 클라이언트요청을 프록시가 받고 인터넷을 거쳐 서버로 보낸다
### 게이트웨이

서로다른 프로토콜을 가진 서버 클라이언트 간의 통신을 중개해주는 역할이다.
프록시도 이게 가능하기 때문에 보안 기능이 없는 프록시는 게이트웨이와 같은 개념으로 쓰인다고 알고 있다.


