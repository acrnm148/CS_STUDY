## HTTP가 뭔지 설명해주세요.
HTTP는 
1. HyperText Transfer Protocol의 약자로
2. 서버-클라이언트 모델을 따르면서
3. request/response 구조로
4. 웹 상에서 text 형태로 정보를 주고받을 수 있는 프로토콜입니다.
5. TCP/IP 기반으로 작동하며,
6. HTTP의 가장 큰 특징은 Connectionless와 Stateless 입니다.


## HTTP
- HTTP는 HyperText Transfer Protocl의 약자로 웹 상에서 정보를 전송하기 위한 통신 프로토콜로써
- HTML과 같은 문서를 전송하는 것에 사용됩니다.
- 클라이언트가 HTTP request를 서버에 보내면 서버는 HTTP response를 클라이언트에게 보내는 구조입니다.
- request message는 start line, headers, body 로 이루어져 있고
  * start line : method, path, HTTP version
  * headers
  * body
- response message는 status line, headers, body 로 이루어져 있습니다.
  * status line : HTTP version, status code, status message
  * headers
  * body
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/5496ff82-415f-4ddf-83e4-71f23d9933f3)



- HTTP는 서버에 연결 후 요청에 대한 응답을 받으면 연결을 끊어버리는 Connectionless 특성을 갖습니다.
  => 장점: 많은 사람들이 웹을 이용하더라도 실제 동시 접속을 최소화하여 더 많은 유저의 요청을 처리할 수 있습니다.
  => 단점: 연결을 끊었기 때문에, 클라이언트의 이전 상태(로그인 유무)를 알 수 없다는 Stateless 특성이 생기게 됩니다.

요청에 대한 응답이 끝나면 연결을 끊어버리는 Connectionless와 정보가 유지되지 않는 Stateless 특성을 가진 HTTP의 단점을 보완하기 위해
cookie, session, jwt 등이 도입되었습니다.


## HTTPS
- HTTP는 정보를 text 형식으로 주고받기 때문에
- 중간에 인터셉트할 경우, 데이터 유출이 발생할 수 있는 문제가 있습니다.
=> 때문에 HTTP에 암호화를 추가한 프로토콜이 HTTPS 입니다.

  
