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
ArgoWorkflows는 Kubernetes에 친화적인 CI/CD 툴로 각 작업을 Pod에서 실행할 수 있고, Workflow를 CR로 작성할 수 있습니다. Kubernetes위에서 작동되는 ArgoWorkflows를 사용하게 되면 컨테이너 기반으로 작동하기 때문에 완전히 격리된 빌드 환경과 재현을 할 수 있습니다. 또한 CR로 Workflow 를 정의할 수 있기 때문에 GitOps와 연결시켜 더욱 선언적으로 CI/CD 환경을 구축할 수 있을것이라고 생각하여 Argo Workflows를 선택하게 되었습니다. 저희 CI/CD의 환경의 경우에는 간단하게 구성되어 있는데요, Argo Workflow Webhook Server를 생성하게 되면 배포 Repository에 Webhook 이 생성되고 커밋이 될 때 마다 event가 발생하여 CI/CD 파이프라인이 작동되게 됩니다. 과정에서는 Kaniko라는 Kubernetes 기반 Docker 없이  Docker Image를 생성할 수 있도록 지원하는 오픈소스를 사용해 어플리케이션을 빌드하고 캐시를 관리합니다. Image 생성 후에는 ArgoCD GitOps 레포지토리에 image tag를 변경하여 배포되게 합니다.

### Link of Thoughts
Area : #1110-Interview 

Keywords :
- 

Related Notes : 
- 