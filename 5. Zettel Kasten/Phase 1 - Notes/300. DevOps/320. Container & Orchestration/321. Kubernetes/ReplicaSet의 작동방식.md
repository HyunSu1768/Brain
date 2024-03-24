---
aliases:
  - Kubernetes
tags:
  - 완료
  - 문헌메모
---


---


Source :
Author : 
URL : https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/

## ReplicaSet의 작동방식
- ReplicaSet을 정의하는 파일에서는 파드를 식별할 수 있는 셀렉터를 정의하고, 몇개의 Pod를 유지할지 개수를 설정하고 개수를 채우기 위해 필요한 파드들의 정보를 포함한 Pod Template도 있다.
- ReplicaSet은 파드의 metadata.ownerReferences 필드를 통해 파드에 연결된다.
- Selector를 사용해서 필요한 새 파드를 식별한다.
- 만약 Pod의 OwnerReferences 필드가 ReplicaSet의 셀렉터와 일치하면 ReplicaSet은 해당 파드를 가지게 된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[ReplicaSet이란]]
- [[Pod란]]
- 