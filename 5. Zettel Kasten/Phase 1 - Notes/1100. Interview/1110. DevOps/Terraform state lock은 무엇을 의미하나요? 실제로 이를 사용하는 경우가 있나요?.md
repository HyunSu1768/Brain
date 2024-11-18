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

## Terraform state lock은 무엇을 의미하나요? 실제로 이를 사용하는 경우가 있나요?
Terraform state lock 파일은 Terraform의 state 파일에 대한 읽기 및 쓰기 행위를 막는것을 말합니다. 이는 state파일의 무결성을 위한 것이며, State가 lock 상태에 있다면 state 파일에 접근할 수 없습니다. User1과 User2가 있다고 했을 때, User1이 terraform apply를 하게되면 terraform state lock 파일이 생기고 User2은 state파일에 접근할 수 없어 terraform apply를 할 수 없게 됩니다. User1이 apply를 끝내면 User2가 terraform state lock 을 획득해 terraform apply를 할 수 있게 됩니다. 이를 통해 여러 유저가 동시에 접근할 때 발생할 수 있는 문제를 해결합니다.

### Link of Thoughts
Area : #1110-Interview/DevOps 

Keywords :
- 

Related Notes : 
- 