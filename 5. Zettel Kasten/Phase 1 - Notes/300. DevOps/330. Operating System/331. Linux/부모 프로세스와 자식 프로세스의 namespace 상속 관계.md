---
aliases:
  - Linux
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## namespace 상속 관계
부모 프로세스가 새로운 자식 프로세스를 생성할 때 2가지 namespace 상속 전략을 가져갈 수 있음
- namespace 공유 (부모와 같은 namespace 사용)
- 새로운 namespace 생성 (자식 프로세스가 새로운 namespace 생성)

## namespace 동작 방식
Linux 에서는 해당 옵션을 설정할 수 있는 System Call을 지원한다.
- clone()
- unshare()

해당 내용은 Kubernetes에서 


### Link of Thoughts
Area : #300-DevOps/330-Operating-System 

Keywords :
- 

Related Notes : 
- [[Namespace란?]]
- [[Namespace의 종류]]