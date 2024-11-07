---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL : https://github.com/kubernetes/enhancements/blob/master/keps/sig-node/4800-cpumanager-split-uncorecache/README.md

https://docs.google.com/document/d/1LpnMjGNsQyHOuVHMktIrjZsdRw9aKZ8djt354nAno6M/edit?tab=t.0

# L3 캐시를 고려한 CPU Manager 개선
이 KEP은 CPU 리소스를 L3 캐시 기준으로 그룹화하는 새로운 CPU Manager 정적 정책 옵션을 제안한다.
이 opt-in 기능은 CPU 할당 알고리즘을 수정하여 L3캐시로 정렬한 후 가능한 한 동일한 L3캐시에 정렬된 CPU를 할당한다. 요청된 CPU 수가 L3 캐시의 그룹화된 CPU 수를 초과한다면 최소한의 L3 캐시로 할당하려고 시도한다. 최적의 정렬이 불가능한 경우에도 이전처럼 워크로드를 허용한다.

## Motivation
현재 kubelet 의 CPU Manager는 분할된 L3 아키텍처를 인식하지 못하고 CPU할당을 여러 L3에 분산시키는 문제가 존재한다.
이로인해 다음과 같은 문제가 발생한다.
- 여러 파드/컨테이너가 동일한 L3캐시를 공유하는 노이지 네이버 문제 발생
- 여러 L3캐시에 걸친 파드는 캐시 간 접근 지연 시간으로 인해 성능 저하
성능 테스트 결과, TPCC/MySQL 워크로드에서 기존 동작 대비 18% 성능 향상, Stream 워크로드에서는 약 20%의 성능 향상을 보임

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- [[CPU L1,  L2,  L3 Cache]]
- [[L3 Cache Group]]
- [[Kubelet이란]]
- [[Noisy Neighbor Problem]]