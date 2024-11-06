---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL : 

## Pod Network Interface
![[Pod Network Interface.png]]
Pod는 여러 컨테이너로 구성되며, Pod 내의 모든 컨테이너는 동일한 네트워크를 공유한다.
Pod내의 컨테이너가 하나의 네트워크 네임스페이스를 공유할 수 있는 이유는 Pause 컨테이너이기 때문이다.
Pause 컨테이너는 Container가 생성되기 전 먼저 생성되어 새로운 namespace, veth 페어를 생성합니다. 이후 container는 pause container를 부모 프로세스로 삼아 부모 프로세스의 namespace를 상속받아 하나의 namespace를 공유하게 됩니다. container의 eth는 veth0와 연결되고, veth0은 외부와 연결되어있는 docker bridge 와 연결되어 외부와 통신할 수 있다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- [[Namespace란?]]
- [[Namespace의 종류]]