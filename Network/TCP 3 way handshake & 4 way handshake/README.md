## TCP 3 way handshake & 4 way handshake


### - TCP의 **3-way handshake - 연결 성립**

![KakaoTalk_Photo_2022-07-29-11-06-38_005](https://user-images.githubusercontent.com/22094204/198688292-a9d3beec-4f23-42f4-a05e-acd9207a597b.jpeg)

1. **SYN 단계** : 클라이언트는 서버에 클라이언트의 ISN을 담아 SYN을 보낸다. ISN은 새로운 TCP 연결의 첫 번째 패킷에 할당된 임의의 시퀀스 번호를 말하며 이는 장치마다 다를 수 있다.
2. **SYN+ACK 단계** : 서버는 클라이언트의 SYN을 수신하고 서버의 ISN을 보내며 승인번호로 클라이언트의 ISN+1을 보낸다.
3. **ACK 단계** : 클라이언트는 서버의 ISN+1한 값인 승인번호를 담아 ACK를 서버에 보낸다.

3-way handshake 과정 이후 신뢰성이 구축되고 데이터 전송을 시작한다. 이 과정 때문에 TCP는 신뢰성이 있는 계층이라고 하며, UDP는 이 과정을 하지 않기 때문에 신뢰성이 없는 계층이라고 한다.

- SYN : Synchronization의 약자, 연결 요청 플래그
- ACK : Acknowledgement의 약자, 응답 플래그
- ISN : Initial Sequence Numbers의 약자, 초기 네트워크 연결을 할 때 할당된 32비트 고유 시퀀스 번호  
  
- - -

### - TCP의 **4-way handshake - 연결 해제**

![KakaoTalk_Photo_2022-07-29-11-06-38_006](https://user-images.githubusercontent.com/22094204/198688281-53fd1577-23fe-48ed-9b0f-7968cae888f1.jpeg)

1. 먼저 클라이언트가 연결을 닫으려고 할 때 FIN으로 설정된 세그먼트를 보낸다. 그리고 클라이언트는 FIN_WAIT_1 상태로 들어가서 서버의 응답을 기다린다.
2. 서버는 클라이언트로 ACK라는 승인 세그먼트를 보낸다. 그리고 CLOSE_WAIT 상태에 들어간다. 클라이언트가 세그먼트를 받으면 FIN_WAIT_2 상태에 들어간다.
3. 서버는 ACK를 보내고 일정 시간 이후에 클라이언트에 FIN이라는 세그먼트를 보낸다.
4. 클라이언트는 TIME_WAIT 상태가 되고 다시 서버로 ACK를 보내서 서버는 CLOSED 상태가 된다. 이후 클라이언트는 어느 정도의 시간을 대기한 후 닫히고 클라이언트와 서버의 모든 자원의 연결이 해제된다.


## 예상질문
- TIME_WAIT 왜 일정 시간 뒤에 닫나?
- SYN / ACK 패킷을 분리하는 이유는?
