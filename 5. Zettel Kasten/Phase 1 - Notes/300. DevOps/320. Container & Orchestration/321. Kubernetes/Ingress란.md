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
URL : https://kubernetes.io/docs/concepts/services-networking/ingress/

## Ingress란?
- 클러스터 안에서 서비스들의 외부 접근을 관리하는 API object이다 (일반적으로 HTTP)
- Load Balancing, SSL 종료, 이름기반 가상 호스팅 기능을 제공한다.
( Ingress는 지원이 종료되었고 새로운 기능인 Gateway API 가 추가됨 v1.19)

- 외부로부터 오는 HTTP HTTPS 요청을 클러스터 내에 있는 서비스로 노출한다
- 임의의 포트나 프로토콜을 노출하지 않으며 HTTP, HTTPS 외 다른 방법으로 노출하고 싶다면 일반적으로 NodePort나 LoadBalancer를 사용한다.
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Service란]]