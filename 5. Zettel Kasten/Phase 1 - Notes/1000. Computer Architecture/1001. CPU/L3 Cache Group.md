---
aliases:
  - Operating System
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## L3 Cache Group
CPU 내에서 L3 Cache Group은 여러개가 존재할 수 있으며, 각 그룹은 독립된 L3 캐시를 가진다. 그룹 내 코어들은 해당 L3캐시를 공유한다.

```
CPU 패키지
├── CCX (CPU Complex) 1
│   ├── L3 캐시 (예: 16MB)
│   ├── 코어 1 (L1 + L2)
│   ├── 코어 2 (L1 + L2)
│   ├── 코어 3 (L1 + L2)
│   └── 코어 4 (L1 + L2)
│
└── CCX 2
    ├── L3 캐시 (예: 16MB)
    ├── 코어 5 (L1 + L2)
    ├── 코어 6 (L1 + L2)
    ├── 코어 7 (L1 + L2)
    └── 코어 8 (L1 + L2)
```
다음과 같은 상황에서 코어 1,2,3,4는 CCX1 의 캐시를 공유하고 코어 5,6,7,8 은 CCX 2의 캐시를 공유한다.
만약 다른 그룹에 캐시에 접근하게 된다면 추가 지연시간이 발생한다.

따라서 하나의 프로그램의 여러 스레드는 하나의 L3 Cache Group 스케줄링되어야 성능이 향상된다.

### Link of Thoughts
Area : #1000-Computer-Architecture/1001-CPU 

Keywords :
- [[CPU]]

Related Notes : 
- [[CPU L1,  L2,  L3 Cache]]