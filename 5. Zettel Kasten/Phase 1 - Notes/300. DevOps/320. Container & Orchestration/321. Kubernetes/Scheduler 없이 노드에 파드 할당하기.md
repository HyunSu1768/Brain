---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 완료
---


---


Source : 뭄샤드 아저씨의 강의
Author : 
URL :

## 수동으로 노드에 파드 할당하기
- Pod 매니페스트 파일에서 spec 아래에 nodeName 으로 설정할 수 있다.

## 만약 Scheduler도 없고 파드에 정의된 nodeName이 없다면
- 파드는 어떠한 노드에 할당되지 않은 채 pending상태에 머무르게 된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- 