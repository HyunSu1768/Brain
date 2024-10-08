---
aliases:
  - SRE
tags:
  - 문헌메모
  - 완료
---


---


Source : Site Reliability Engineering ( P. 41 )
Author : 
URL :

## 개발자와 SRE의 대립
서비스 개발자들은 개발 실적에 도움되도록 새로운 코드를 가능한 빨리 배포하기를 원한다.
하지만 SRE는 신뢰성을 중요시 하기때문에 많은 양의 변경사항을 배제하려는 경향이 있다.
### 의견 대립
#### 소프트웨어 결함 허용
- 예상하지 못한 이벤트가 발생하였을때 소프트웨어의 유연성을 얼마나 확보해야 할까?
#### 테스트
- 테스트를 충분히 하지 않을 경우에는 결함이 있는 소프트웨어가 탄생할 수 있고, 또한 너무 많은 테스트를 진행할 시 시장에 나설 기회가 줄어들 수 있다.
#### 출시 빈도
- 새로운 코드를 출시하는 것은 언제나 위험을 감수해야한다. 이 위험 부담을 줄이는 것과 다른 작업을 수행하는 것의 균형을 어떻게 맞출 수 있을까?
#### 카나리 테스트 빈도와 규모
- 카나리 테스트는 코드를 릴리즈 하긴 전 일부 트래픽만 테스트 해보는 것으로 이미 모범 사례로 널리 알려진 방법이다. 카나리 테스트는 얼마나 오래 해야하며, 규모를 어떻게 설정해야 할까?

이러한 의견을 토대로 양쪽 모두 동의할 수 있는 지표를 설정해야 하며, 의사 결정은 데이터에 기반할수록 더욱 나은 결정이 될 수 있다.

### Link of Thoughts
Area : #300-DevOps/360-Site-Reliability-Engineering 

Keywords :
- [[SRE]]

Related Notes : 
- 