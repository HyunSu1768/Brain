---
aliases:
  - Datadog
tags:
  - 300-DevOps/370-Monitoring
  - 완료
---


---


Source :
Author : 
URL : https://hyuckang.tistory.com/96

## Datadog Integration이란?
- Integration : 통합
- 통합은 모니터링 대상을 Datadog과 assemble 하는 개념
- 여러가지 데이터가 Datadog으로 들어올 때 Datadog은 해당 데이터를 어떤 방식으로 해석해야할지 모름, Datadog은 Integration을 통해 모니터링 대상을 보다 정확하게 파악할 수 있다.

## Integration의 3가지 유형
- Agent-Based
	- Datadog Agent에 기반한 통합으로, check라는 파이썬 클래스 메서드를 사용하여 수집할 메트릭을 정의한다.
- Authentication(crawler) based
	- datadog이 직접 모니터링 대상을 크롤링하여 통합하는 방식
- Library
	- datadog API를 호출하는 클라이언트 코드를 사용하여 통합하는 방식

### Link of Thoughts
Area : #300-DevOps/350-Monitoring 

Keywords :
- 

Related Notes : 
- [[Datadog Agent이란]]
- [[Datadog 이란]]