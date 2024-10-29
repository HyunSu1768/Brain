---
aliases:
  - Kuberentes
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL : https://kubernetes.io/ko/docs/concepts/scheduling-eviction/taint-and-toleration/
뭄샤드 아저씨의 강의 

## Taint
- 노드에 파드가 배치될 수 있는 조건을 명시함 ( 필터 )
만약 노드에 key1=value1:NoSchedule 이라는 taint가 존재한다고 가정했을때 파드에 일치하는 toleration이 없으면 스케줄되지 않는다.(NoSchedule)

## Master 노드에 파드가 배치되지 않는 이유
마스터 노드는 기본적으로 ```
```
node-role.kubernetes.io=master:NoSchedule
```
해당 taint를 가지고 있어 파드가 스케줄되지 않는다.
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- 