# Blocking, Non-blocking & Synchronous, Asynchronous

### Q1. Non-Blocking과 Asynchronous의 차이점
> Non-Blocking은 호출된 함수가 자신의 작업이 종료되지 않아도 제어권을 호출한 함수에게 넘겨줘 호출한 함수가 작업을 할 수 있도록 해줍니다. 
> 
> Asynchronous는 호출한 함수는 해당 작업의 결과 값을 상관하지 않고, 호출된 함수가 콜백으로 결과 값을 넘겨주는 방식 등으로 결과 처리를 하는 것입니다. 
>
> Non-Blocking은 제어의 관점, Asynchronous는 작업 완료 여부를 신경쓰는 유무의 관점으로 봐야합니다. 

### Q2. Synchronous/Asynchronous와 Blocking/Non-Blocking의 차이점
- Synchronous/Asynchronous
    - Synchronous
        - **요청한 순서가 지켜지는 것**
            - 3개를 요청했을 때, 응답에서 순서가 지켜집니다. 
        - 호출한 함수가 호출된 함수의 작업 완료 여부를 계속 체크하는 것입니다. 
    - Asynchronous
        - **요청한 순서가 지켜지지 않은 것**
            - 3개를 요청했을 때, 어떤 요청에 대한 응답이 올 지 알 수 없습니다. 
        - 호출한 함수가 호출된 함수의 작업 완료 여부를 신경쓰지 않으며, 작업 완료가 되면 callback 등의 형태로 호출된 함수가 호출한 함수에게 알려줍니다. 
- Blocking/Non-Blocking
    - Blocking
        - 호출된 함수가 호출한 함수에게 제어권을 주지 않습니다. 
        - 따라서 호출한 함수는 호출된 함수의 일이 끝날 때까지 기다려야합니다. 
    - Non-Blocking
        - 호출된 함수가 호출한 함수에게 제어권을 줍니다.
        - 따라서 호출한 함수는 호출된 함수의 결과를 기다리면서 다른 일을 진행할 수 있습니다. 
