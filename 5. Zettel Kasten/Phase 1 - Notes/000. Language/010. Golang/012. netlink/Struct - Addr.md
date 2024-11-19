---
aliases:
  - Golang
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Addr Struct
```
// Addr represents an IP address from netlink. Netlink ip addresses// include a mask, so it stores the address as a net.IPNet.  
type Addr struct {  
    *net.IPNet  
    Label       string  
    Flags       int  
    Scope       int  
    Peer        *net.IPNet  
    Broadcast   net.IP  
    PreferedLft int  
    ValidLft    int  
    LinkIndex   int  
}
```

Addr 구조체는 netlink로부터 가져온 IP 주소 정보를 나타낸다. Netlink는 Linux 커널과 사용자 공간 간의 통신을 위한 인터페이스로, 네트워크 구성 정보를 조회하거나 설정할 때 사용됨. Addr 구조체는 IP주소와 그와 관련된 다양한 속성을 저장함

### 필드
- \*net.IPNet
	- IP주소와 서브넷 마스크를 포함하는 표준 라이브러리
- Label
	- IP 주소에 대한 식별자로, 일반적으로 네트워크 인터페이스의 이름을 나타낸다.
- Flags
	- IP주소와 관련된 속성을 나타내는 플래그
- Scope
	- IP 주소의 범위를 나타낸다.
		- 인터넷에서 접근 가능한지, 로컬 네트워크 내에서만 유효한지, 특정 조직 내에서만 유효한지
- Peer \*net.IPNet
	- P2P 링크의 상대방 주소를 나타낸다.
- Broadcast net.IP
	- 해당 네트워크의 브로드캐스트 주소를 나타낸다.
	- x.x.x.255
- PreferedLft
	- IP 주소가 선호 상태로 유지되는 기간을 초 단위로 나타낸다.
- validLft
	- IP 주소가 유효한 상태로 유지되는 기간을 초 단위로 나타낸다.
- LinkIndex
	- IP 주소가 속한 네트워크 인터페이스의 인덱스
	- [[Struct - Interface]]의 Index와 동일함

### Link of Thoughts
Area : #000-Language/010-Go 

Keywords :
- 

Related Notes : 
- [[Struct - Addr]]