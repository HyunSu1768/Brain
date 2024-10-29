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
URL : https://github.com/kubernetes/kubernetes/pull/128348

## 문제상황
현재 9 CPU 를 필요로 하는 pod-high-priority-large-cpu.yaml 을 사용중인데, 주어진 노드는 4 CPU만을 가지고 있어 해당 파드가 선점될 수 없음.

## 문제 해결
테스트 케이스가 3CPU를 필요로 하는 pod-high-priority.yaml 을 사용하게 하여 해결.


### Link of Thoughts
Area :

Keywords :
- 

Related Notes : 
- 