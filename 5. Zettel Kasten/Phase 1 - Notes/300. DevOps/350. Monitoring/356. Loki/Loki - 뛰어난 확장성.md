---
aliases:
  - Loki
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## 뛰어난 확장성
1. Object Storage 기반 설계
	- Loki는 Local Disk 대신 Cloud Object Storage에 로그를 저장하기 때문에 큰 제약없이 스토리지를 확장할 수 있다.
2. 모듈러 아키텍처
	- Distributor : 로그 수집 -> 필요 시 수평 확장
	- Ingester : 로그를 임시 저장 후 chunking -> 수평 확장 가능
	- Querier : 쿼리 요청을 병렬로 실행
	- Query Frontend : 쿼리 병렬화 및 캐싱 : 대규모 쿼리도 빠르게 처리
	- 이렇게 모듈화 되어있어 각 기능에 대해 특정 역할만 스케일 아웃 할 수 있어 확장성이 뛰어남

### Link of Thoughts
Area : #300-DevOps/350-Monitoring 

Keywords :
- [[Loki]]

Related Notes : 
- [[Loki란?]]