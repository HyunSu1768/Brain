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
URL : https://no-easy-dev.tistory.com/entry/%EC%BF%A0%EB%B2%84%EB%84%A4%ED%8B%B0%EC%8A%A4-Pod-%EC%9E%90%EC%9B%90%EA%B4%80%EB%A6%AC-QoS

## QoS Class
파드의 리소스 사용을 관리하기 위해 파드의 리소스 요청 및 제한 설정에 따라 지정되는 품질 등급이다.
QoS Class 를 통해 우선 순위를 정하고 리소스를 보다 효율적으로 관리함

### Guaranteed
requests와 limits이 동일하게 설정되면 이 클래스가 적용된다. 가상 높은 우선순위를 가지고 있어 리소스가 부족한 경우에도 마지막으로 축출된다.

### Burstable
requests와 limits이 다르게 설정된 경우, 또는 모든 컨테이너가 requests는 설정했지만 limits가 없는 경우 이 클래스가 적용된다. 우선순위는 Guaranteed 클래스보다 낮다.

### BestEffort
requests와 limits 모두 설정되지 않은 경우 이 클래스가 적용된다. 리소스가 부족할 때 가장 먼저 축출된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- 