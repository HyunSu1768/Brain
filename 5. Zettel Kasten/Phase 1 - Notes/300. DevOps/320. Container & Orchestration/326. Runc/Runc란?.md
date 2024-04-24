---
aliases:
  - Runc
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL : https://velog.io/@koo8624/Docker-OCI-and-runc

## Runc란?
- 저수준 컨테이너 런타임으로 Namespace, Cgroups을 실제로 나누는 역할을 하며 프로세스를 실행합니다.
- 컨테이너, 즉 프로세스의 라이프사이클을 관리합니다.
runc 는 containerd 에서 실제로 격리된 환경에서 컨테이너를 실행할 수 있도록 하기 위해 사용되고 있습니다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[runc]]

Related Notes : 
- [[Namespace란?]]
- [[Cgroup(Control Group) 이란?]]
- [[containerd]]