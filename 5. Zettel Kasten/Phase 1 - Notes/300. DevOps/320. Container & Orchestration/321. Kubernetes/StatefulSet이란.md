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
URL : https://kubernetes.io/ko/docs/concepts/workloads/controllers/statefulset/

## StatefulSet이란
- 애플리케이션의 상태유지를 위한 워크로드 API 오브젝트
- Deployment의 기능을 포함하고 있음
- Deployment와 달리 파드들의 순서를 보장해 주고 각 파드들은 고유 식별자를 가짐
	- Deployment에서 파드의 개수를 2개 이상으로 설정하였을때 각 파드는 다 다른 IP를 가지지만 해당 IP 를 통해서는 파드가 무엇을 나타내는지에 대한 정보를 알 수없지만 Stateful에서는 IP에 DNS를 할당하여 각 파드들을 식별할 수 있도록 함
- Deployment와 동일하게 파드들은 같은 스팩을 가짐

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Deployment란]]
- [[Workload란]]