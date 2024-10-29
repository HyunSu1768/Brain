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
URL : 뭄샤드 아저씨

## LoadBalancer란?
- 외부 로드밸런서와 함께 사용된다. ( AWS, Azure, GCP )
- NodePort, ClusterIP 모두 자동으로 생성된다.
- 클라우드 환경이 아닌 VM이나 온프레미스 환경에서 클러스터를 운영한다면 별로의 로드밸런서 구현이 필요하다 ( MetalLB또는 LoadBalancer에 수동으로 loadBalancerIP를 공유기의 공인 IP로 지정 후 네트워크 설정에서 포트포워딩 하는 방법도 있음 <- 귀찮다. )
- NodePort는 노드의 IP를 알아야 Pod에 접근할 수 있지만 LoadBalancer는 클라우드에서 제공해주는 도메인을 사용하기 때문에 보다 쉽게 접근할 수 있음

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Service란]]