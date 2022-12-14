# TCP/IP 흐름제어 & 혼잡제어
### Q1. 흐름제어와 혼잡제어에 대해 간략히 설명하세요
```
흐름 제어: 수신 측의 데이터 처리 속도와 송신 측의 데이터 전송 속도 간의 차이를 해결하기 위해 전송한 패킷(들)에 대한 ACK을 받으면 다음 패킷(들)을 보내는 것 

혼잡 제어: 송신 측의 데이터 전송 속도와 네트워크의 데이터 처리 속도의 차이를 해결하기 위해 혼잡 상태가 발생하면 window 크기를 줄이는 것 
```
### Q2. 흐름제어 기법 중 하나인 stop and wait 방법이 잘 사용되지 않는 이유는?
```
패킷을 하나씩만 보내기에 비효율적이기 때문입니다. 
```
### Q3. TCP 통신에서 흐름제어와 혼잡제어를 하는 이유는?
```
TCP 통신은 ✨신뢰성을 보장하는 통신✨을 하기 때문에 신뢰성 보장을 하기 위해 
송수신자 간의 TCP 버퍼 크기 차이로 인해 생기는 데이터 처리 속도 차이를 해결하기 위해 흐름 제어를 사용합니다.

송신 측에서 보내는 데이터의 양이 라우터가 처리할 수 있는 양을 초과하면 초과된 데이터는 라우터가 처리하지 못합니다. 송신 측은 초과된 데이터를 손실 데이터로 간주하고 계속 재전송하여 네트워크를 혼잡하게 하는데, 이러한 상황을 예방하기 위해 송신 측의 전송 속도를 적절히 조절하는 혼잡 제어 기법을 사용합니다. 
```