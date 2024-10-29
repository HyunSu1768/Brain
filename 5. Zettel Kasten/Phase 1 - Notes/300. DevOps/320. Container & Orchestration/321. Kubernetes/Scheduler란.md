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
URL : 뭄샤드 아저씨의 강의

## Scheduler란?
- 파드가 어떤 노드에 배치되어야 할 지 결정함
- 스케쥴러는 파드가 어떤 노드에 배치되어야 할지를 결정하지, 파드를 직접 배치하지는 않음 (배치하는건 kubelet의 역할)
## 순서
1. 먼저 파드의 리소스 사용량을 보고 (Cpu, Memory) 파드의 리소스 사용량만큼의 리소스가 없는 노드들을 걸러냄
2. 만약 리소스 사용량만큼의 리소스가 있는 노드가 여러개라면 노드의 Rank를 매김 Rank를 매기는 방식은은 만약 해당 노드에 파드가 배치되었을때 남은 리소스를 Rank로 하고 Rank가 높은 노드가 선정됨

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Kubelet이란]]