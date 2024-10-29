---
aliases:
  - Docker
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Low Level Build ( 저수준 빌드 )
LLB는 Buildkit의 핵심 중간 표현으로, 빌드 프로세스를 상세하고 구조적으로 표현한다.
LLB 는 빌드 단계와 그 사이의 의존성을 나타내는 DAG(Directed Acyclic Graph)로 구성되어 있음

### LLB 특징
- 언어 및 도구 중립성 : 특정 빌드나 도구에 종속되지 않는다.
- 최적화 용이성 : 빌드 단계를 재배열하거나 병렬화하기 쉽다.
- 캐싱 효율성 : 각 단계의 입력과 출력을 명확히 정의하여 적중률을 높인다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Docker]]

Related Notes : 
- [[Buildkit - 구조]]
- [[Buildkit - 개념]]