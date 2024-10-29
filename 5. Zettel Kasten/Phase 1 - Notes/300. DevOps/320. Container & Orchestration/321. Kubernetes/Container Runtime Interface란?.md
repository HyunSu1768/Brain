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
URL : https://kubernetes.io/ko/docs/concepts/architecture/cri/

## Container Runtime Interface란?
- Kubelet이 다양한 컨테이너 런타임을 사용할 수 있도록 하는 인터페이스
	- containerd, CRI-O 등
- Kubelet과 컨테이너 런타임 사이의 통신을 위한 프로토콜이다
- Kubelet과 컨테이너 런타임 사이의 통신을 위한 gRPC 프로토콜을 정의한다

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[gRPC란?]]