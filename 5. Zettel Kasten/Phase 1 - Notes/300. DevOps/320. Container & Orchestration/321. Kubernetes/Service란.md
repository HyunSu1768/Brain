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
URL : 뭄샤드 아저씨

## Service란?
- 파드 집합에서 실행중인 애플리케이션을 네트워크로 노출하는 추상화된 방법
- 파드 자체에도 IP가 주어지지만, 만약 Auto Scaling 되거나 IP가 변경되었을때 문제가 생김 
- 따라서 Service 계층을 거쳐서 파드와 통신하게 됨

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Ingress란]]
- [[ClusterIP란]]
- [[LoadBalancer란]]