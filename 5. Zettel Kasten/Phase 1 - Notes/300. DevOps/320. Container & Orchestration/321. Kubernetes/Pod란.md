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
URL :


# Pod

- Kubernetes가 작동하는 실행 단위는 Pod이며 Pod는 컨테이너들의 집합입니다.
- Pod는 단일 IP를 가지며 볼륨을 공유합니다.
- 예를 들어 웹 파드에는 웹서비스가 중심이 되는 컨테이너가 있을 수 있고, 거기에서 발생하는 로그를 추적하여 외부 인프라로 전달하는 컨테이너가 있을 수 있습니다.

파드는 JSON이나 YAML 로 작성될 수 있으며 pod manifest라고 불립니다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Pod 사용 예시]]
- [[Pod Network Interface]]

