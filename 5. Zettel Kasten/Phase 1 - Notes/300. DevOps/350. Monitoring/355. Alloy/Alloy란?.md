---
aliases:
  - Alloy
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL : https://hackjsp.tistory.com/78

## Alloy란?
기존 Prometheus, OpenTelemetry 등 다양한 메트릭 수집 주체를 하나로 통합해 하나의 Agent에서 로그, 메트릭, 트레이스를 수집할 수 있게 구축된 Grafana 생태계의 백엔드 시스템임. 하나의 Agent에서 수집하여 다양한 데이터 소스로부터 필요에 따라 처리 후 Grafana, Grafana Tempo, 등등으로 전송할 수있음

### 특징
- OTel, Prometheus, Pyroscope, Loki 등 다양한 메트릭, 로그, 트레이스 등 프로파일링 도구에 대한 기본 파이프라인 제공
- 호환성 : OTel Collector, Prometheus Agent, Promtail 과 완벽하게 호환
- 리소스 효율성 : Prometheus 대비 1/10 수준의 리소스로 메트릭 수집 가능
- LGTM 지원 : Loki, Grafana, Tempo, Mimir 스택과 원활하게 연동

### Link of Thoughts
Area : #300-DevOps/350-Monitoring 

Keywords :
- [[Alloy]]

Related Notes : 
- 