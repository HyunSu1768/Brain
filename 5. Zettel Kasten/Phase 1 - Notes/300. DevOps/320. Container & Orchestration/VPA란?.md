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

## VPA란?
- Pod 의 AutoScaling 을 담당하는 k8s의 custom resource 이다.
- HPA 와 달리 수평적 확장인 아닌, 수직적 확장을 제공한다.
- CPU, Memory 의 사용량을 모니터링하여 이를 기반으로 적절한 사용량을 지정한 뒤 Pod를 생성한다.

## VPA 구성요소
- Recommender
	- Pod의 실제 CPU, Memory 사용량을 모니터링하고 Pod의 리소스 권장값을 제공한다.
- Updator
	- Pod가 Recommender에 의해 설정된 권장값으로 설정되어있는지 확인하고, 그렇지 않다면 Admission Controller가 권장값으로 파드를 다시 생성할 수 있도록 Pod를 종료시킵니다.
- Admission Controller
	- Pod의 리소스 요청을 Recommender가 권장한 값으로 설정한다.

### Link of Thoughts
Area :

Keywords :
- 

Related Notes : 
- 