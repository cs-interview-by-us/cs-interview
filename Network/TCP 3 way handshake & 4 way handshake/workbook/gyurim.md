# TCP 3 way handshake & 4 way handshake 워크북 
### Q1. TIME_WAIT 왜 일정 시간 뒤에 닫나?
```
IP 프로토콜의 문제점인 순서보장이 없기 때문에 TIME_WAIT이 있어야합니다. 
즉, TIME_WAIT 상태가 존재함으로써 접속 종료를 요청하는 클라이언트가 마지막으로 송신하는 응답 메세지(ACK)에 문제가 발생할 경우 재송신이 가능합니다. 재송신된 ACK을 수신한 서버는 정상적으로 CLOSED 상태가 될 수 있습니다. 
```
### Q2. SYN / ACK 패킷을 분리하는 이유는?
```
TCP 특성인 신뢰성을 보장하기 위해 SYN/ACK 패킷을 분리합니다. 
```
### Q3. Selective ACK과 Cumulative ACK란?
```
TCP가 여러 개의 패킷을 전송할 때, 가운데 패킷이 유실된 경우,

Cumulative ACK은 유실된 패킷부터 다시 재전송해달라는 의미로 사용하는 ACK 입니다.  따라서 (1, 2, X, 4, 5, 6, 7)이 보내졌다고 했을 때, 3부터 재전송되어 이미 보내진 4, 5, 6, 7도 재전송됩니다. 

Selective ACK은 수신 측에 잘 도착한 패킷 시퀀스✨에 대해 알려줘서 송신 측이 SACK을 통해 알게된 손실 패킷을 재전송할 수 있도록 돕는 것입니다.  
```