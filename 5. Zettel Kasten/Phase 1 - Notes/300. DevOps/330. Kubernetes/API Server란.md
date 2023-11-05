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

# API Server
- Control Plane의 핵심이다
- 클러스터에 속한 노드 혹은 외부의 사용자로부터 HTTP API Request를 받아 클러스터의 상태를 관리하는 기능을 수행한다
- 사용자와 클러스터 간 상호작용이 가능하도록 해준다
- 우리가 일반적으로 생각하는 CRUD서버랑 똑같다고 보면 됨 여기에 요청을 보내서 생성,삭제,수정 등을 할 수 있는것

## API 서버의 주요 기능
- RESTFul API
	- RESTFul API를 통해 클라이언트와 통신한다
	- CRUD 기능을 한다.
- 인증(Authentication)
	- API서버는 클러스터에 액세스하는 사용자와 요청을 인증한다.
	- 인증을 위해 다양한 방법이 존재하며 권한에 맞게 리소스에 접근할 수 있다.
- 권한 부여 (Authorization)
	- 인증된 사용자의 요청에 맞게 권한을 부여하고 검사하는 역할을 한다.
	- Kubernetes는 RBAC, ABAC란 등 다양한 권한 부여 방식을 지원한다.
- 승인(Admission)
	- API Server는 사용자 요청을 처리하기 전에 승이 단계를 거친다.
	- 승인 컨트롤러는 클러스터에 영향을 미치기 전에 해당 요청이 적절한지 검사하고, 필요시 해당 요청을 거부, 수정할 수있다.
- API Object 저장 및 관리
	- API Server 는 클러스터의 리소스를 etcd라는 분산 key-value 저장소에 저장하고 관리한다.
	- etcd는 클러스터의 상태를 일관성 있게 유지하고 각 컴포넌트 사이에서 공유하기 위한 데이터 저장소이다.


### Link of Thoughts
Area : #300-DevOps/330-Kubernetes 

Keywords :
- 

Related Notes : 
-  [[etcd란]]
-  [[Kubernetes란]]
- [[Control Plane란]]
