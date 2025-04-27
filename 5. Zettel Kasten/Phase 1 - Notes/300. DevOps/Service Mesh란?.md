---
aliases: 
tags:
---


---


Source :
Author : 
URL :

## Service Mesh가 생기게된 계기?
1. MSA의 등장
	- Docker 이후에 소프트웨어의 아키텍처는 MSA가 보편적인 아키텍처로 자리잡게 되었다. MSA 는 수십 수백개의 서비스끼리 통신해야 하는데, 네트워킹, 로깅, 인증, 리트라이 같은 공통 문제가 매번 개발자가 처리해야 했다. 
2. Sidecar 패턴의 등장
	- 이 문제를 해결하기 위해 나온 개념이 Sidecar 패턴이다. 애플리케이션 컨테이너 옆에 네트워킹을 담당하는 Container를 붙여 어플리케이션에서는 네트워킹을 신경쓰지 않고도 Sidecar가 이를 대신해준다.
3. Service Mesh의 등장
	- Sidecar라는 개념이 나오게 되면서 이를 조직적으로 운영할 수 있도록 돕는 Serivce Mesh라는 아키텍처가 생기게 되었다. 
	- 만약 Sidecar만 사용하고 Service Mesh를 사용하지 않는다면, 하나의 설정을 변경할 때도 각 서비스의 설정을 모두 업데이트 해야하고, 디버깅, 트러블슈팅도 어렵다.
	- Service Mesh를 사용한다면 컨트롤 플레인이 있기 때문에 각 서비스에 직접적으로 Sidecar를 설정하지 않아도 중앙에서 통합 관리할 수 있으며 모니터링, 트래픽 시각화까지 한번에 볼 수 있다.


### Link of Thoughts
Area : #300-DevOps 

Keywords :
- 

Related Notes : 
- [[Docker 이후의 생태계 변화]]