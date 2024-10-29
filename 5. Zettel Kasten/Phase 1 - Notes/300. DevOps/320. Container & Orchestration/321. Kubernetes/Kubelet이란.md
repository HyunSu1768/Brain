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
URL : 뭄샤드 아저씨의 강의

# Kubelet
![[Pasted image 20231029221641.png]]
- 각 노드에서 실행되는 [Node Agent란](Node%20Agent란.md)
- [API Server란](API%20Server란.md)와 통신한다.
- Worker Node가 배라면 kubelet은 선장이다.
- 노드에서 컨테이너가 동작하도록 관리해 주는 핵심 요소
- 워커노드의 에이전트이다.
- 주기적으로 container의 상태를 API Server에 보고함
## 작동방식
1. 쿠버네티스 파드를 관리하기 위해 YAML을 작성한다.
2. kubectl 명령어를 통해 해당 명령을 쿠버네티스 클러스터에 적용한다.
3. 이때 yaml 명령이 [API Server란](API%20Server란.md)로 전송된 후 kubelet으로 전송된다.
4. kubelet은 이 YAML을 통해 전달된 pod를 생성 혹은 변경하고, 이후 생성된 yaml에 명시된 컨테이너가 정상적으로 실행되고 있는지 확인한다.

## 기능
- 파드에서 컨테이너가 실행되게 한다. [Control Plane란](Control%20Plane란.md)에서 노드에 작업을 요청하는 경우 kubelet이 작업을 수행한다.
- [API Server란](API%20Server란.md) 와 통신하며, Pod Spec을 사용해 Pod Spec에 기술된 컨테이너들이 정상적으로 작동되도록 돕는다
- 선언된 상태와 일치하지 않는 Pod가 있는지 확인하고, 어떤 Node에 Pod를 배치할지 정한다.
- 어디에 배치할 지는 Scheduler가 결정하지만 Container Runtime(Docker)에 배치하는 명령하는 것은 kubelet이 담당한다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Control Plane란]]
- [[API Server란]]
- [[Node Agent란]]

