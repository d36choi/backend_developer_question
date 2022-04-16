## HTTP 응답 코드 중 4xx/5xx는 어떻게 다른가 ?

> A 4xx code indicates an error caused by the user, whereas 5xx codes tell the client that they did everything correctly and it’s the server itself who caused the problem.
> 

에러의 유발원인에 따라 다르다.

400 → user 의 잘못이므로 알려줘야함. 500 → 서버의 잘못이고 클라이언트는 옳게 요청보냈음.

## restful api 를 설명하라

### HTTP to CRUD
POST : Create
GET : Read
PUT,PATCH : Update
DELETE : Delete

### put, fetch 차이
### GET,POST 의 차이가 뭔거같냐?
