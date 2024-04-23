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
URL :https://hasensprung.tistory.com/178, [https://en.wikipedia.org/wiki/Completely_Fair_Scheduler](https://en.wikipedia.org/wiki/Completely_Fair_Scheduler)

해당 글은 CFS에 대한 아주 간단한 글이며 실제 동작방식은 보다 복잡할 수 있습니다.

## Completely Fair Scheduling 이란?
- Linux 커널에서 사용되는 CPU Scheduling Algorithm으로, 모든 프로세스가 CPU 점유 시간을 공정하게 ( 균등하게 ) 나누어 가질 수 있도록 하는 알고리즘 이다.
- linux kernel 6.6 부터 eevdf 알고리즘으로 대체되었다.

## CFS 핵심 개념
### vruntime
- vruntime은 가상 런타임으로 이는 프로세스가 실제로 CPU를 얼마나 사용했는지를 나타냅니다.
 CFS는 가상 런타임이 가장 낮은 프로세스부터 CPU에 할당하여 모든 프로세스가 공평하게 시간을 받도록 할당합니다.
### 레드-블랙 트리
- 위에서 말했던 것처럼 CFS 알고리즘은 vruntime이 가장 낮은 프로세스를 찾아야 하는데, 레드-블랙 트리를 통해 vruntime이 가장 낮은 것부터 정렬하여 더 vruntime이 가장 낮은 프로세스를 빨리 찾을 수 있도록 합니다.
### Time slice
- CFS는 프로세스의 우선순위와 시스템의 부하에 따라 Time slice를 동적으로 조절하고, 더 많은 프로세스가 CPU에 접근할 수 있도록 합니다.

### Link of Thoughts
Area : #300-DevOps/330-Operating-System 

Keywords :
- [[Linux]]

Related Notes : 
- 