### Q1. HTTP와 HTTPS의 차이점은?

|  | HTTP | HTTPS |
| --- | --- | --- |
| 보안 | 무담보 | O |
| 암호화 | X | O |
| 증명성 | 필요 X | 필요 O |
| 계층 | 응용 | 전송 |
| 포트번호 | 80 | 443 |
| 예시 | 인터넷 포럼, 교육 사이트와 같은 웹 사이트 | 은행 웹 사이트, 결제 게이트웨이, 쇼핑 웹 사이트 등의 웹 사이트 |

### Q2. SSL이란?

Secure Socket Layer이라는 약자로 보안 소켓 레이어이다.

웹서버와 웹 브라우저 간의 보안을 위해 만들어졌으며,

공개키 방식으로 대칭키를 암호화하고 실제 데이터를 주고 받을 때는 대칭키 기반으로 사용함

### Q3. SSL과 CA는 어떤 관계가 있나요?

클라이언트가 서버에 접속하면, 서버가 클라이언트에게 SSL 인증서(공개키+개인키(server 소유))를 전달함

CA의 개인키로 암호화된 이 SSL인증서를 이미 모두에게 공개된 CA의 공개키를 사용하여 복호화함

복호화에 성공하면 이 인증서는 CA가 서명한 것이 맞는 것 즉, 인증서를 검증해 안전하게 사용할 수 있음