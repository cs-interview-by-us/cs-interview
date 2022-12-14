# 로드밸런싱

둘 이상의 CPU or 저장장치와 같은 컴퓨터 자원들에게 작업을 나누는 것

(* 로드(Load) : 서버가 받는 부하(traffic))

![Untitled](https://user-images.githubusercontent.com/22094204/201196977-b8e095f3-0135-46d3-a726-3810428534de.png)

요즘 시대에는 웹사이트에 접속하는 인원이 급격히 늘어나게됨

따라서 이 사람들에 대해 모든 트래픽을 감당하기엔 1대의 서버로는 부족함. 대응 방안으로 하드웨어의 성능을 올리거나(Scale-up) 여러대의 서버가 나눠서 일하도록 만드는 것(Scale-out)이 있음

하드웨어 향상 비용이 더욱 비싸기도 하고, 서버가 여러대면 무중단 서비스를 제공하는 환경 구성이 용이하므로 Scale-out이 효과적. 이때 여러 서버에게 균등하게 트래픽을 분산시켜주는 것이 바로 **로드 밸런싱**

**로드 밸런싱**은 여러 대의 서버로 트래픽(Load)을 균등하게 분산(Balancing)해주는 역할을 함. Load Balancer를 클라이언트와 서버풀 사이에 두고, 부하가 일어나지 않도록 여러 서버에 분산시켜주는 방식. 서비스를 운영하는 사이트의 규모에 따라 서버를 추가로 증설하면서 로드 밸런서로 관리해주면 서버의 부하를 해결할 수 있음

</br>

### **로드 밸런서가 서버를 선택하는 방식**

- 라운드 로빈(Round Robin) : CPU 스케줄링의 라운드 로빈 방식 활용
- Least Connections : 연결 개수가 가장 적은 서버 선택 (트래픽으로 인해 세션이 길어지는 경우 권장)
- Source : 사용자 IP를 해싱하여 분배 (특정 사용자가 항상 같은 서버로 연결되는 것 보장)

</br>

### **로드 밸런서 장애 대비**

서버를 분배하는 로드 밸런서에 문제가 생길 수 있기 때문에 로드 밸런서를 이중화하여 대비한다.

![Untitled 1](https://user-images.githubusercontent.com/22094204/201196986-90e1e24c-3737-4603-9df3-1a673ce6f3e0.png)

> Active 상태와 Passive 상태
>
