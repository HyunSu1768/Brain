---
aliases:
  - SRE
tags:
  - 문헌메모
  - 완료
---


---


Source : Site Reliability Engineering ( P. 54 )
Author : 
URL :

## SLO는 기대치를 설정하는 것
SLO를 정한다는 것은 서비스에 대해 목표치를 설정하는것과 같다고 할 수 있다.
예를 들어 시스템의 상황에 따라 SLO가 변할 수 있다. 문서를 저장하는 시스템은 물론 가용성, 내구성 모두 중요하지만 문서의 내구성을 지키는 것이 더 중요하다고 생각할 수 있다.

사용자의 현실적인 기대치를 설정하려면 아래 두 가지 중 하나 혹은 모두를 고려해야 한다.
### 안전 제한선을 지킬 것
- 사용자들에게 광고한 SLO 보다 내부적으로는 더 보수적인 SLO를 설정하는것이 좋다. SLO를 더 높게 설정해 만성적으로 발생하는 문제들이 외부로 노출되기 전에 적절하게 대응할 수 있기 때문이다.

### 지나친 목표를 설정하지 말 것
- 만약 실제 공개된 SLO 보다 실제 서비스의 성능이 더 뛰어나다면, 해당 서비스는 현재 성능에 계속 의존하게 된어 사용자들이 더 높은 기대치를 가지게 된다.
- SLO보다 실제 서비스의 성능이 뛰어나다면 개발자들의 개선의지를 잃게 만들 수 있다.


### Link of Thoughts
Area : #300-DevOps/360-Site-Reliability-Engineering 

Keywords :
- [[SRE]]

Related Notes : 
- [[Service Level Objectives ( SLO )]]
- [[Service Level Indicator ( SLI )]]