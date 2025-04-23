---
aliases:
  - Docker
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Docker 이후의 생태계 변화
### DevOps 문화의 확산
- DevOps는 개발과 운영의 경계를 흐리게 했다. 동일한 이미지가 개발, 테스트, 환경에서 재사용 되었기 때문에 개발자들은 운영 환경을 위한 코드를 작성하였고 운영자는 개발자의 의도를 이해할 수 있게되었다.

### CI/CD 자동화
- 컨테이너 이미지 빌드, 테스트, 배포가 파이프로 연결되었다.

### MSA의 정착
- 이미지로 쉽게 어플리케이션 배포 환경을 만들 수 있게 되었고 컨테이너는 작은 단위의 서비스로 나누어 운영하기 적합했다. 또한 각 서비스는 독립된 컨테이너로 관리되어, 스케일 아웃에 유리하다.

### Kubernetes의 등장
- MSA가 정착하면서 수백개의 마이크로서비스를 관리해야 했다. 이를 달성하기 위해서는 스케줄링, 로드밸런싱, 상태 관리 등이 필요한데 이 문제를 해결한 것이 Kubernetes이다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Docker]]

Related Notes : 
- [[Container 기술의 철학과 진화]]