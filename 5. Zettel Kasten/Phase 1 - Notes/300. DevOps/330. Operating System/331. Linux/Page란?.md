---
aliases:
  - Linux
tags:
  - 문헌메모
  - 완료
---


---


Source : 모던 리눅스 43 P
Author : 
URL : 

## Page
리눅스에서는 프로세스는 물리적으로 가지고 있는 메모리보다 더 많은 가상 메로리를 얻는데, 이 가상 메모리를 4KB 사이즈로 분할 하는 단위이다.

### Page Table
페이지 테이블은 가상 메모리의 페이지를 물리적 메모리의 페이지와 매핑할 수 있도록 한다.

### TLB
CPU가 프로세스의 가상 페이지에 접근할 때마다 CPU는 프로세스가 사용하는 가상 주소를 이에 해당하는 물리적 주소로 변환해야 한다. 이 프로세스의 속도를 높이기 위해 최신 아키텍처는 TBL(translation lookaside buffer) 라는 조회용 온칩을 지원한다.


### 메모리 정보
```
cat /proc/meminfo
```

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Linux]]

Related Notes : 
- 