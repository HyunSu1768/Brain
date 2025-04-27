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

## Answer
원래는 Github Action 만으로 CI 환경을 제공하였지만, 서비스 수가 많아짐에 따라서 분산된 CI 환경을 관리하기 어려워 졌습니다. 따라서 플랫폼 엔지니어링을 하는 여러 사례들을 찾아봤고 찾아본 회사 모두 GoCD를 사용하고 있어 무작정 GoCD를 선택하고 적용하였습니다. 하지만 정작 해결하고 싶었던 CI 관리 환경의 통합만이 아닌 CD 환경까지 모두 통합해버려 기존 GitOps의 완벽한 구현의 한계가 있었고 또한 Build Cache 관리포인트가 늘어가 서비스가 많아짐에 따라 운영 부담이 커졌습니다. 또한 DevOps 팀이 많지 않고 학교를 다니며 모두 관리하기 힘들었습니다. 따라서 문제정의를 다시 하고 최적의 CI/CD 환경으로 마이그레이션 하기 위해 Ci 환경 통합은 Kubernetes 기반 Argo Workflows 를 선택하고 CD 툴로는 ArgoCD를 사용하도록 마이그레이션 하였습니다.

### Link of Thoughts
Area : #1110-Interview 

Keywords :
- 

Related Notes : 
- 