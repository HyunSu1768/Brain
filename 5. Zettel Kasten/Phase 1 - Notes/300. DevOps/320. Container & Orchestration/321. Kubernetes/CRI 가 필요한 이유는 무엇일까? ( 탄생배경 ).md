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
URL : https://kubernetes.io/blog/2016/12/container-runtime-interface-cri-in-kubernetes/#:~:text=Before%20starting%20a%20pod%2C%20kubelet%20calls%20RuntimeService.RunPodSandbox%20to%20create%20the%20environment

## Container Runtime Interface가 필요한 이유?
Container Runtime Interface가 나타나게 된 이유는 간단합니다.
kubernetes 사용자들은 다양한 contianer runtime을 사용하고 싶어하였습니다.
Kubernetes 1.5 버전에는 kubelet을 재컴파일 할 필요 없이 CRI를 도입하였습니다.
1.3 버전에서는 rkt, docker와 같은 컨테이너 런타임에 대한 사용을 kubernetes 내부 코드에서 작성하여 컨테이너 런타임의 변경에 매우 취약하여 CRI가 탄생하게 되었습니다.
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Kubelet이란]]
- [[Container Runtime Interface란?]]