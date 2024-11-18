---
aliases:
  - Interview
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Replication Controller 란 무엇인가요?
Replication Controller는 RC의 지정된 replica를 유지하기 위해 사용됩니다. 만약 replica를 3으로 설정했다면 Replication Controller는 이를 유지하기 위해 Pod를 생성합니다. Pod는 같은 여러 노드에 분산되어 생성될 수 있습니다. 이를 통해 수평적 확장을 구현할 수 있게 됩니다. 하지만 Replication Controller를 사용한다고 해서 트래픽이 많아졌을때 자동으로 확장하는 기능을 제공하진 않습니다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- [[Replication Controller란]]