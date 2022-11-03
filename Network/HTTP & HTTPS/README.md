# HTTP & HTTPS

### HTTP(HyperText Transfer Protocol)

인터넷 상에서 클라이언트와 서버가 자원을 주고 받을 때 쓰는 통신 규약

HTTP는 텍스트 교환이므로,
누군가 네트워크에서 신호를 가로채면 내용이 노출되는 **보안 이슈**가 존재
-> 이런 보안 문제를 해결해주는 프로토콜 : *HTTPS*

---

### HTTP****S(HyperText Transfer Protocol Secure)****

인터넷 상에서 정보를 암호화하는 *SSL 프로토콜을 위에 HTTP 프로토콜을 얹어 **보안된 HTTP 통신 규약**

<img src="https://user-images.githubusercontent.com/22094204/199591802-d3d6eeea-1013-4b82-8804-3c98354e5465.png" width="400px" height= "100px" />

*SSL : 공개키 암호화 방식을 이용해 문서를 보완함

(SSL→TLS : ‘보안 계층’이라는 독립적인 프로토콜 계층을 만들어, 응용계층과 전송 계층 사이에 속함)

---

무엇으로부터 **안전**할까? → 2가지

1. **내가 사이트에 보내는 정보들을 제 3자가 못 보게 함**
    
    ex. naver에 접속해서 id, pw입력하고 로그인 버튼 누르면 인터넷을 타고 naver 서버에 전송됨
    
    <img src="https://user-images.githubusercontent.com/22094204/199592692-d839e1c1-038c-45f0-b22a-8056e27ae5d2.png" width="300px" height= "150px" />
    
    HTTP는 id : ~, pw: ~ 텍스트 입력한 대로 보내짐
    
    <img src="https://user-images.githubusercontent.com/22094204/199592706-85d537b4-a9ac-497a-8022-db4d31c0c95c.png" width="300px" height= "150px" />
    
    HTTPS는 텍스트를 암호화함 (*공개키 암호화 방식으로)
    
    간단하게 *공개키 방식은
    
    A키로 암호화 하면 B키로만 복호화 가능
    
    <img src="https://user-images.githubusercontent.com/22094204/199592749-4308f721-41b6-4cb0-a0ff-6148156b7046.png" width="300px" height= "40px" />
    
    반대로, B키로 암호화를 하면 A키로만 복호화 가능
    
    <img src="https://user-images.githubusercontent.com/22094204/199592759-e29e0068-2313-4095-b1dd-f9f83a3b5678.png" width="300px" height= "40px" />
    
2. **접속한 사이트가 신뢰할 수 있는 사이트인지 알려줌**

(기관으로부터 검증된 사이트만 주소에 HTTPS 사용이 허가됨)

---

****HTTPS 통신 흐름****

[서버와 CA]

1. 서버 만드는 기업(S)은 공개키와 개인키를 만들어 **개인키를 보관**함
2. 신뢰할 수 있는 *CA 기업을 선택하고, 그 기업에게 내 **공개키 관리를 부탁**하며 계약함

(*CA : Certificate Authority로, 공개키를 저장해주는 신뢰성이 검증된 민간기업)

3. 계약 완료된 CA 기업은 해당 기업의 이름, (S)서버 공개키, **공개키 암호화 방법을 담은 인증서를** 만들고, 해당 인증서를 **CA기업의 개인키로 암호화**해서 (S)서버에게 제공함

[서버와 클라이언트]

4. (S)서버는 암호화된 인증서를 갖게됐음. 이제 (S)서버는 (S)서버의 공개키로 암호화된 HTTPS요청이 아닌 요청이 오면, 이 암호화된 인증서를 클라이언트에게 건내줌
5. 클라이언트가 `main.html` 파일을 달라고 (S)서버에 요청했다고 가정! 
    1. HTPPS 요청이 아니기에 **클라이언트**는 CA기업이 (S)서버의 정보를 **CA기업의 개인키로 암호화한 인증서**를 받게됨(4번 참고)
    2. **CA 기업의 공개키**는 브라우저가 이미 알고있음(브라우저가 인증서를 탐색하여 해독이 가능한 것)
6. 브라우저는 해독한 뒤 (S)서버의 공개키를 얻게 됨. 이제 A서버와 통신할 땐, 얻은 A서버의 공개키로 암호화해서 요청을 날리게 됨(⇒ 대칭키 사용)

</br>
  
HTTPS도 무조건 안전한 것은 아니다. (신뢰받는 CA 기업이 아닌 자체 인증서 발급한 경우 등)

이때는 HTTPS지만 브라우저에서 `주의 요함`, `안전하지 않은 사이트`와 같은 알림으로 주의 받게 된다.  

</br></br>

[참고]

[얄코 - HTTPS](<https://www.youtube.com/watch?v=H6lpFRpyl14&t=301s](https://www.youtube.com/watch?v=H6lpFRpyl14&t=301s>)
