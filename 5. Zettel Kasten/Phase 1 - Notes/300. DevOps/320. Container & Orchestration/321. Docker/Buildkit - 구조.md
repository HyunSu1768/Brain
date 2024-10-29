---
aliases:
  - Docker
tags:
  - 문헌메모
---


---


Source :
Author : 
URL : 

## Buildkit 구조
buildkit의 구성 요소는 여러개로 나뉘어져 있고, 각 요소는 빌드 프로세스의 특정 부분을 담당

### Frontend
- Dockerfile, Buildpack 등 고수준의 빌드 정의를 저수준 빌드 정의로 표현
- 기능
	- 빌드 스크립트를 파싱하고 분석
	- 빌드 작업을 설명하는 표현인 LLB(Low Level Build)로 변환

### Solver
- Frontend에서 변환된 LLB를 받아 빌드 프로세스를 최적화하고 실행 계획을 수립
- 기능
	- LLB의 DAG(Directed Acyclic Graph) 구조를 분석
	- 의존성을 파악하고 병렬 실행 가능성 평가
	- 캐시를 활용하여 중복 작업 제거

### Executor
- Solver에서 수립한 실행 계획에 따라 실제로 빌드 작업을 수행
- 기능
	- 각 빌드 단계에서 필요한 작업을 실행 (COPY, RUN etc..)
	- 다양한 실행 환경(containerd, runc) 지원
	- 격리된 환경에서 안전한 빌드 환경 지원

### Cache
- 빌드 작업의 결과를 저장하고 재사용하여 빌드 효율성 증가
- 기능
	- **콘텐츠 기반 주소 지정**을 사용하여 데이터 무결성 보장
	- 로컬 캐시 및 원격 캐시를 지원하여 다양한 환경에서의 캐시 활용 가능
	- 레이어 중복 제거를 통해 이미지 크기 최적화

### Distributor
- 빌드 결과물을 다양한 형태로 출력하거나 배포
- 기능
	- Docker Image 로 출력하거나, OCI 이미지 형식으로 저장
	- 빌드 아티팩트를 파일 시스템이나 외부 저장소에 저장
	- 멀티플랫폼 빌드 이미지 생성, 배포

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Docker]]

Related Notes : 
- [[Buildkit - 개념]]
- [[Buildkit - 컨텐츠 기반 주소 지정 - CAS(Content Addressable Storage)]]
- [[Buildkit - LLB (Low Level Build)]]