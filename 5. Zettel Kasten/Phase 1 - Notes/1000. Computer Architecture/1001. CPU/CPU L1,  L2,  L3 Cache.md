---
aliases:
  - Computer Architecture
tags:
---


---


Source : 
Author : 
URL :

CPU 에서 사용하는 Cache는 CPU와 Memory 사이에서 속도 간극을 줄여주는 것으로, L1, L2, L3 Cache로 나뉜다.
## L1 Cache
- 가장 빠르고 CPU에 가까운 캐시
- 일반적으로 32KB-64KB
- 명령어 캐시(I-Cache)와 데이터 캐시(D-Cache)로 분리
- 접근 지연시간 : 약 1 ~ 3 사이클
- CPU 코어마다 독립적으로 존재

## L2 Cache
- L1보다 크고 느린 중간 계층의 캐시
- 보통 256KB ~ 1MB 크기
- 통합된 캐시로 명령어와 데이터 모두 저장
- 접근 지연시간 : 약 10~20 사이클
- 코어별로 별도 존재하거나 일부 코어가 공유

## L3 Cache
- 가장 큰 용량의 마지막 단계 캐시
- 보통 2MB ~ 64MB 크기
- 모든 코어가 공유하는 통합 캐시
- 접근 지연시간 : 약 40~ 75 사이클

## 비교
- 용량 : L1 < L2 < L3
- 속도 : L1 > L2 > L3
- 가격 : L1 > L2 > L3



### Link of Thoughts
Area : #1000-Computer-Architecture/1001-CPU 

Keywords :
- [[CPU]]

Related Notes : 
- 