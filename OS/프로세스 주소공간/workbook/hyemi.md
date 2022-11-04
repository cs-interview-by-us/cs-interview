# 프로세스 주소공간  
## Q1. 프로세스 주소공간의 4가지 영역은?  
> 프로세스의 주소공간은 Text(Code), Data, Stack, Heap 4가지 segment로 구성되어 있습니다.  

## Q2. 프로세스 주소공간을 나누는 이유는?  
> 메모리는 한정되어 있기 때문에 데이터를 공유하여 __메모리를 절약하기 위해서__ 입니다.  
>   
> Stack Segment와 Data Segment를 구분한 이유는 역할의 분배(stack의 구조) 때문입니다.  
> Stack Segment는 LIFO 특성을 가졌기 때문에 Stack Segment를 통해 함수의 흐름을 관리하고, static 변수와 어떤 함수에서도 접근할 수 있는 전역 변수는 Data 영역을 통해 관리합니다.  
