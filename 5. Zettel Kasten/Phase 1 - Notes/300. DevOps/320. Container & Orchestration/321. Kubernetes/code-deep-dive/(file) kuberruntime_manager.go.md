---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 완료
---


---


Source : pkg/kubelet/kuberruntime/kuberruntime_manager.go
Author : 
URL :

## kuberruntime_manager.go 의 역할
- kuberruntime_manager.go 파일은 kubernetes kubelet에서 컨테이너 런타임 관리를 위한 핵심 로직을 포함한 파일이다. 이 파일은 kubelet의 파드 생애주기를 관리할 수 있도록 하며, 여러 컨테이너 런타임을 일관되게 관리할 수 있도록 추상화 하는 역할을 함

### kubeGenericRuntimeManager
- kuberruntime_manager.go 파일 안에 포함되어 있는 구조체
다양한 컨테이너 런타임을 추상화 하여 공통된 인터페이스로 접근할 수 있도록 도와준다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- 