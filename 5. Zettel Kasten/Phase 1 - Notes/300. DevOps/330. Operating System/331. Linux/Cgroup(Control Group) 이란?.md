---
aliases: 
tags:
---
프

---


Source :
Author : 
URL : https://velog.io/@whattsup_kim/Linux-Kernel-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%A6%AC%EB%88%85%EC%8A%A4%EC%9D%98-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EA%B2%A9%EB%A6%AC-%EA%B8%B0%EB%8A%A5-cgroup-namespace-union-mount

## Cgroups이란?
- 프로세스들이 사용하는 시스템의 자원의 사용 정보를 수집, 제한, 격리하는 리눅스 커널 역할을 함
- /sys/fs/cgroup 디렉토리에 관련 설정들이 있음.
- Namespace 를 나누면서 cgroup도 같이 설정해 주면 cpu, memory 격리와 더불어 프로세스들 끼리도 격리할 수 있기 때문에 거의 완벽하게 격리할 수 있음

### Link of Thoughts
Area : #300-DevOps/330-Operating-System 

Keywords :
- [[Linux]]

Related Notes : 
- [[Namespace란?]]
- [[Cgroup(Control Group) 이란?]]