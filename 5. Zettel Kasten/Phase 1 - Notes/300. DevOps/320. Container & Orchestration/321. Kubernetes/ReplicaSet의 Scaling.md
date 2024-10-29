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
URL : https://kubernetes.io/ko/docs/concepts/workloads/controllers/replicaset/

## ReplicaSet의 Scaling방법
- .spec.relicas 의 수를 조절하면 ReplicaSet은 사용자가 지정한 파드의 개수를 유지하려고 하기 때문에 해당 필드를 조절한다면 Pod의 개수를 의도한대로 유지하며 운영할 수 있다.

### Scale Down 시 우선순위

1. Pending 상태의 Pod를 먼저 삭제된다.
2. controller.kubernetes.io/pod-deletion-cost 어노테이션이 설정되어있는 파드들은 낮은 값을 가지는 Pod가 Scale Down 된다.
3. 더 많은 Replica가 있는 노드의 파드가 더 적은 Replica가 있는 노드의 파드보다 먼저 Scale Down 된다.
4. 파드의 생성 시간이 다르다면, 더 최근에 생성된 파드가 먼저 Scale Down 된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[ReplicaSet이란]]
- [[ReplicaSet의 작동방식]]