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

# Deployment
- ReplicaSet의 상위 개념으로 Pod와 ReplicaSet에 대한 배포를 관리한다.
- 애플리케이션이 부하가 늘어가 Pod의 개수를 늘려야 할 때 개수를 늘리는 등 여러가지 동작을 Deployment로 관리할 수 있다.
- Pod에 대한 기준 Spec을 정의한다.
- Deployment를 통해서 생성하는 것을 권장하고 있으며, Pod와 ReplicaSet의 기준 정보를 지정할 수 있다.
- Pod가 Scale in,out 되는 기준을 정의한다.
- ReplicaSet의 기능에서 버전관리 즉 배포전략을 설정할 수 있다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Pod란]]
- [[ReplicaSet이란]]


