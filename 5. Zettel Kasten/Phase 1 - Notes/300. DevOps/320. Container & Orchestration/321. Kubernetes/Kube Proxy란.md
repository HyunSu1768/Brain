---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 진행중
---
	

---


Source :
Author : 
URL : 뭄샤드 아저씨의 강의와 블로그

## Kube Proxy란?
- 파드간 통신을 가능하게 해줌
- DaemonSet 형태로 배포되어 모든 노드에서 파드 형태로 kube-proxy를 가짐
- 파드들의 통신을 가능하게 해야 하기 때문에 hostNetwork 옵션을 true로 함으로써 노드 자체의 네트워크를 사용함 ( CNI 를 생성하지 않음 )


### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[DaemonSet이란]]
- [[DaemonSet의 사용 용도]]