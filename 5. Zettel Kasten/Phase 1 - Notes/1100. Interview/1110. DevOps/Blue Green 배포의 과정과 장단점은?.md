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

## Blue/Green 배포의 과정과 장단점은?
Blue/Green 배포는 새로운 버전의 환경과 운영 환경을 동시에 올리는 기법입니다. Blue 환경에는 현재 운영중인 서버가 실행되고 Green 환경에는 새롭게 배포된 서버가 올라가게 됩니다. 새롭게 배포된 서버를 Green 환경에 올려 테스트와 검증을 거친 후 DNS, LoadBalancer의 라우팅 설정을 Green 환경의 서버로 변경하여 무중단 배포를 구현할 수 있습니다. 만약 새로운 환경에서 치명적인 오류가 발생하면 즉시 이전 환경으로 트래픽을 전환하여 롤백할 수 있습니다. Blue Green 배포의 단점은 운영 환경과 새로운 버전의 운영 환경이 같이 올라가기 때문에 인프라와 서버의 리소스 자원이 2배 더 사용될 수 있다는 단점이 있습니다.

### Link of Thoughts
Area : #1110-Interview/DevOps 

Keywords :
- DevOps

Related Notes : 
- 