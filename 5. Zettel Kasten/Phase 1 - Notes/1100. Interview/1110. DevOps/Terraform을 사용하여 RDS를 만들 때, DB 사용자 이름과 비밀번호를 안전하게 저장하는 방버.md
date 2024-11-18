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

먼저 DB Username, Password는 Github 저장소에 평문화된 채로 저장되면 안됩니다. 사용자 이름과 비밀번호를 안전하게 저장하는 방법은 크게 2가지가 있는데요, 첫번째로는 Terraform Cloud의 사용입니다. Terraform Cloud를 사용해 리소스를 배포한다면 Terraform Cloud 내에 있는 Secret관리 기능을 사용할 수 있습니다. 두번째로는 같은 회사의 제품인 Vault를 사용하는 것 입니다. Vault를 사용해 중요한 정보를 안전한 장소에 저장하고, Terraform과 통합하여 필요할 때 꺼내씁니다.

### Link of Thoughts
Area : #1110-Interview/DevOps 
Keywords :
- Terraform

Related Notes : 
- 