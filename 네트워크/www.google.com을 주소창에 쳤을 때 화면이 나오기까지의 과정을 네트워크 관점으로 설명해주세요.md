## 웹 동작 방식

1. 유저가 브라우저에서 www.google.comm(URL)을 입력하면 HTTP request message HTTP 요청메시지를 생성합니다.
2. IP주소를 알아야 전송을 할 수 있으므로, DNS lookup을 통해 해당 도메인의 server IP 주소를 알아냅니다.
3. 반한된 IP주소(구글 서버 IP)로 HTTP 요청메시지 전송 요청을 합니다.
   - HTTP 요청메시지를 TCP/IP 층에 전달합니다.
   - HTTP 요청메시지에 헤더를 추가해서 TCP/IP 패킷을 생성합니다.
4. 해당 패킷은 전기신호로 랜선을 통해 네트워크로 전송되고, 목적지 IP에 도달합니다.
5. 구글 서버에 도착한 패킷은 unpacking을 통해 요청메시지를 복원하고 서버의 process로 보냅니다.
6. 서버의 process는 HTTP 요청메시지에 대한 응답 데이터(response data)를 가지고 HTTP 응답 메시지를 생성합니다.
7. HTTP 응답 메시지를 전달 받은 방식 그대로 client IP로 전송합니다.
8. HTTP response 메시지에 담긴 데이터를 토대로 웹브라우저에서 HTML 렌더링을 하여 모니터에 검색창이 보여집니다.


![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/8f2c6c1e-3605-4ae2-b770-ec03a8e6590b)


