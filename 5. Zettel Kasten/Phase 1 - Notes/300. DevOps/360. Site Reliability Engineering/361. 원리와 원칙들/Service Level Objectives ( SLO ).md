---
aliases:
  - SRE
tags:
  - 문헌메모
  - 완료
---
 

---


Source : Site Reliability Engineering ( P. 46 )
Author : 
URL :

## Service Level Objectives ( 서비스 수준 목표 )
- SLI 에 의해 측정된 서비스 수준의 **목표** 값 혹은 **일정 범위**의 값을 의미한다.
- SLI 의 지표를 토대로 서비스에서 지켜야 할 목표를 정하는 것을 의미한다.

다음과 같은 예시가 있다.
- 검색 결과를 빠르게 리턴하도록 원한다.
	- SLO를 100밀리초 이하로 설정한다.

하지만 이렇게 SLO를 쉽게 정할 수 없다. HTTP 요청에 경우 QPS(Query Per Second) 는 사용자의 수에 따라 결정되는 것이기 때문에 이 지표에 대한 SLO를 설정하는 것은 말이 되지 않는다.

SLO를 설정하고 이를 사용자에게 공개하는 것은 서비스의 동작을 예측할 수 있게 된다. 서비스가 갑자기 느려졌다는 근거없는 불평을 줄일 수 있다.

명확한 SLO를 설정하지 않았을때, 서비스를 개발하고 운영하는 사람들의 의견이 맞지 않아 희망하는 성능이 나오지 않거나 혹은 목표를 초과할 수도 있다.
### Link of Thoughts
Area : #300-DevOps/360-Site-Reliability-Engineering 

Keywords :
- [[SRE]]

Related Notes : 
- [[Service Level Indicator ( SLI )]]
- [[가용성]]
- [[목표 가용성 수준]]