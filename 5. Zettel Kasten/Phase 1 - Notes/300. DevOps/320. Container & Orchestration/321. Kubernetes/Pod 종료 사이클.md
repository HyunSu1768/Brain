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

## 프로세스
1. Pod 종료 요청
	- kubectl delete pod와 같은 명령이나, 컨트롤러(Deployment, StatefulSet etc..)를 삭제했을때 Pod 종료가 시작된다.
2. API Server에 삭제 요청
	- API Server는 파드 종료 요청을 수신하면 Pod Status에 deletionTimeStamp 를 설정하여 Pod가 삭제중임을 표시한다.
	- API Server는 이 시점에 kubelet이 Pod를 즉시 삭제하지 않도록 하기 위해 grace period를 지정한다. 기본적으로 30초의 시간이 주어지며, 이 시간동안 kubelet이 정리 작업을 할 수 있는 시간을 확보한다.
3. kubelet 종료 신호 수신 및 프로세스 정리 시작
	- API 서버가 Pod의 deletionTimeStamp를 설정한 뒤, kubelet이 이 update를 감지하면 해당 Pod의 종료 프로세스를 시작한다.
		- PreStop Hook 실행 : Pod에서 PreStop Hook 이 설정되어있는 경우 해당 명령을 실행한다.
		- SIGTERM 신호 전송 : kubelet은 Pod의 컨테이너에게 SIGTERM 신호를 보내 애플리케이션이 graceful하게 종료될 수 있도록 한다.
		- grace period 대기 : kubelet은 grace period 동안 Pod가 graceful하게 종료되기를 기다리고, 이 기간동안 종료되지 않으면 다음 단계로 넘어간다.
		- SIGKILL 신호 전송 : grace period 시간이 지나면 Pod를 종료하기 위해 SIGKILL 신호를 전송한다.
4. . Endpoints와 Service에서 Pod 제거
	- kubelet이 종료 프로세스를 진행하는 동안, API Server는 서비스에서 Pod를 제거하는 작업을 수행한다. 이를 통해 Service에서 더 이상 종료된 파드에 요청이 가지 않도록 한다.
5. Pod 리소스 삭제
	- kubelet이 모든 컨테이너를 종료하고 grace period가 만료되면, API Server에서 Pod 리소스가 최종적으로 삭제된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes란]]

Related Notes : 
- [[Pod란]]
- [[Pod종료에 대한 고찰]]