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

## Answer
KubeSpray는 Ansible 기반 Cluster Orchestration 도구로 Cluster를 쉽게 프로비저닝 할 수 있도로 도와주는 도구입니다. 간단한 설정만으로 HA, ETCD, Node Join, CNI 를 설정할 수 있으며 각 노드의 운영체제가 다르더라도 모두 호환되는 리소스를 자동으로 선택하고 설치하기 때문에 초기 구축 상황과 추후 확장이 필요할 때도 쉽게 구성할 수 있습니다. 실제로 KubeSpray 테스트 과정에서 AMD 기반 HP 서버와 ARM 기반 라즈베리파이 노드로 테스트를 진행하였는데 ARM이 지원되지 않은 구성요소들에 대한 처리를 하기만 하면 모두 정상적으로 작동하였습니다. 또한 클러스터 설정을 Yaml로 설정하기 때문에 클러스터 구성 상태를 코드로 관리할 수 있다는 장점이 있어 KubeSpray를 사용하게 되었습니다.

### Link of Thoughts
Area : #300-DevOps 

Keywords :
- 

Related Notes : 
- [[Kube Spray란?]]