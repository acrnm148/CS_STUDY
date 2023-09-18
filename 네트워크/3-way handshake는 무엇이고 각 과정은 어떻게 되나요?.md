# 3-way handshake는 무엇이고 각 과정은 어떻게 되나요?
- 3-way handshake는 TCP/IP 프로토콜로 통신하기 전, 정확한 정보 전송을 위해 상대방 컴퓨터와 연결하는(세션을 수립하는) 과정입니다.
  (TCP 연결 초기화)
  1. 클라이언트가 서버에게 접속을 요청하는 SYN(syncronize) 패킷을 보내면,
  2. 서버는 요청을 수락하는 ACK()를 포함하여, SYN + ACK 패킷을 클라이언트에게 발송합니다.
  3. 클라이언트가 이것을 수신한 후, 다시 서버에게 ACK 패킷을 발송하면
  4. 연결이 이루어지고, 이제부터 데이터를 주고받을 수 있습니다.

## 우리가 네이버에 접속할 때마다
네이버의 서버와 나의 노트북은 3-way handshake를 하면서 서로를 확인하게 됩니다.

## 3-way handshake의 목적
- 서로를 확인하고 연결하기 위한 절차이다.

## TCP 3 way handshake
TCP 통신은 3단계의 과정을 거칩니다.
1. Connection setup : TCP 연결 초기화 단계입니다. -> 3-way handshake가 일어납니다.
2. Data transfer : 데이터 전송 단계입니다.
3. Connection termination : TCP 연결 종료 단계입니다. -> 4-way handshake가 일어납니다.

3-way handshake는 Connection setup의 과정입니다.
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/1a784584-b1b1-4bf9-b2db-208314dd6bc8)

SYN : Synchronize Sequence Number
- 요청을 보낸다
ACK : Acknowlodgements
- 요청을 수락한다

