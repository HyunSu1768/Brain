---
aliases:
  - Kong
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Kong 이란?
Kong은 오픈소스 API Gateway로, 다음과 같은 기능을 통해 API Gateway역할을 한다.
- 트래픽 라우팅
- 인증/인가
- 로깅
- 속도 제한
- 로드 밸런싱
- 플러그인 시스템 지원 등
	- Lua Script를 통해 req/res 의 라이프사이클에 개입할 수 있다.

## Kubernetes와 Kong
Kubernetes에서는 Kong Ingress Controller로 배포하여 API Gateway로 사용한다.
- 구성요소
	- Kong Proxy : 실제 트래픽을 처리하는 API Gateway
	- Kong Ingress Controller : K8s Ingress 를 감지하고 Kong에 설정 반영
	- Kong Manager ( Enterprise ) 
	- PostgreSQL ( DB mode )

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kong]]

Related Notes : 
- [[Kong Controller 란?]]
- [[KongProxy란?]]