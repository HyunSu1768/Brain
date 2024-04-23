---
aliases: 
tags:
---


---


Source :
Author : 
URL : https://nginxstore.com/blog/kubernetes/%EB%84%A4%EC%9E%84%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%99%80-cgroup%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%A9%EB%8B%88%EA%B9%8C/

## Namespace란?
- 프로세스를 서로 격리할 수 있게 함
- 하나의 프로세스 집합은 하나의 리소스 집합을 보게 하고, 다른 프로세스 집합은 이전에 말했던 리소스 집합이 아닌 또 다른 리소스 집합을 보게 함으로써 프로세스가 격리되도록 함. ( 리눅스 커널의 기능 )

## VM과의 차이점
- VM은 Hypervisor를 통해 OS 까지 따로 두어 격리하는 반면 Namespace를 통한 격리 방법은 하나의 OS에서 커널의 기능을 사용하여 격리하는 것이기 때문에 오버헤드가 적다.

### Link of Thoughts
Area : #300-DevOps/330-Operating-System 

Keywords :
- [[Linux]]

Related Notes : 
- [[Hypervisor란?]]