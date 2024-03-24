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
URL : https://kubernetes.io/ko/docs/concepts/workloads/controllers/job/

## Job이란?
- 잡에서는 하나 이상의 파드를 생성하고 지정된 수의 파드가 성공적으로 종료될 때가지 게속해서 파드의 실행을 재시도한다.
- 지정된만큼의 성공 수를 도달하면 Job이 완료된다.
- Job이 실행도중 중단되면 다시 재게될 때까지 파드는 삭제되고 Job이 다시 시작되면 파드가 생성된다.
- 잡을 사용하면 파드를 병렬로 실행할 수 있다.
- 잡을 스케줄에 따라 구동하고 싶은 경우 CronJob을 사용한다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- 