## OSI 7계층과 TCP/IP 4계층을 비교하여 설명해주세요.
- OSI 7계층은 네트워크 통신을 표준화한 모델입니다. 통신 시스템을 7단계로 나누어 설명한 것입니다.
- OSI 7계층은 실무적으로 이용하기에는 복잡한 탓에
  실제 인터넷에서는 이를 단순화한 TCP/IP 4계층이 사용되고 있습니다.


## OSI 7계층과 TCP/IP 4계층
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/5b3da536-83e3-4f1e-a408-b78614428914)

OSI 7계층과 TCP/IP 4계층 모델에서
- 각 계층은 하위 계층의 기능을 이용하고, 상위 계층에게 기능을 제공합니다.
- 일반적으로 상위계층의 프로토콜은 소프트웨어, 하위계층의 프로토콜은 하드웨어로 구현됩니다.

-> 예를 들어, HTTP 프로토콜은 TCP 프로토콜과 IP 프로토콜을 이용해서 작동합니다.
-> 물리계층은 전기신호로 통신이 이루어집니다.

## 캡슐화(Encapsulation) & 역캡슐화(Decapsulation)
캡슐화란,
통신 프로토콜을 사용하기 위한 정보를 Header에 포함시켜 하위계층에 전송하는 것입니다.
역캡슐화란,
통신 상대 측에서 이러한 Header를 역순으로 제거하면서 원래의 Data를 얻는 과정입니다.

예를 들어, 사용자는 최상위 계층인 응용계층에서 인터넷접속(HTTP), 메일전송(SMTP), 파일전송(FTP), 원격로그인(Telnet) 등의 작업을 수행합니다.
![image](https://github.com/acrnm148/CS_STUDY/assets/67724306/e4acc1e7-469b-42ed-885b-402551884ffe)

- 사용자가 전송하고자 하는 데이터는 **각 프로토콜을 사용하기 위한 정보를 Header에 포함**시켜서 **하위 계층에 전달**합니다. (캡슐화)
  => 이것은 최종적으로 **물리계층에서 binary 데이터로 변환되어 전송**됩니다.
- 상대측에서는 이러한 **Header를 역순으로 하나씩 제거**하면서 **상위계층으로 데이터를 전달**합니다. (역캡슐화)
  => 최종적으로 원본데이터를 수신하게 됩니다.


