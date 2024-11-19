---
aliases:
  - Golang
tags:
  - 문헌메모
  - 완료
---


---


Source : go net 패키지
Author : 
URL :

## Interface 구조체
```
type Interface struct {  
    Index        int          // positive integer that starts at one, zero is never used  
    MTU          int          // maximum transmission unit  
    Name         string       // e.g., "en0", "lo0", "eth0.100"  
    HardwareAddr HardwareAddr // IEEE MAC-48, EUI-48 and EUI-64 form  
    Flags        Flags        // e.g., FlagUp, FlagLoopback, FlagMulticast  
}
```
네트워크 인터페이스를 뜻한다.
### 필드 역할
- Index : 시스템에서 인터페이스의 고유 번호가 부여된다. 인터페이스의 번호는 1부터 시작한다.
- MTU : maximum trasmission unit의 준말로, 전송 패킷의 최대 크기를 지정함
- Name : 인터페이스의 이름으로 en0, lo0 veth0 등의 이름을 가질 수 있음
- HardwareAddr : MAC 주소나 EUI-48, EUI-64 형식으로 표기됨
- Flags : 인터페이스의 상태를 나타냄 ( Flagup : 활성, FlagLoopback : 루프백 인터페이스, FlagMulticast : 멀티캐스트 가능 여부)
### Link of Thoughts
Area : #000-Language/010-Go 

Keywords :
- 

Related Notes : 
- [[Network Interface란?]]