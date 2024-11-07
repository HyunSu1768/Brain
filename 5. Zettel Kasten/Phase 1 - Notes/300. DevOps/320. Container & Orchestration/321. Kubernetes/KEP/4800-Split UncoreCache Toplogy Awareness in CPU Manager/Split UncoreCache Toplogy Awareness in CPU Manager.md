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

## 목표
1. 파드와 컨테이너 범위에서 동일한 L3 캐시 그룹 내에서 CPU를 할당하는 새로운 CPU Manager 정책 옵션 추가
2. 서로 다른 L3 캐시 그룹에서의 CPU 자원 할당 최소화
3. 멀티 소켓 시스템 자원 추가

## 목표가 아닌 것
1. CPU Manager 정책이 'none'으로 설정된 경우는 수정하기 않는다.
2. fill-pcpus-only와 같은 기존 정적 정책 옵션의 동작은 변경하지 않음

## Proposal
- uncore cache grouping 에 대한 선호도를 가지는 새로운 정적 정책 추가
- Topology 구조체에 이미 포함된 CPUDetails에 새로운 멤버인 uncorecacheId를 추가하여 CPU가 속한 언코어 캐시를 추적
- pkg/kubelet/cm/cpumanager/policy_options.go 에서 정책 옵션 활성화 처리 및 시스템 지원 여부 확인
- 기존 Allocate 정적 정책에 "prefer-align-cpus-by-uncorecache" 옵션 적용 로직 추가
- 향후 "distribute-cpus-across-numa" 및 "distribute-cpus-across-cores" 정책과의 호환성 계획

## User Stories
**Story 1**
- HPC 사용자로서 최대 성능을 내고 지연 시간을 줄이고 싶습니다. 정적 CPU Manager 정책을 사용하지만, 분할 언코어 캐시 프로세스에서는 언코어 캐시 간 할당으로 인해 지연 시간이 발생합니다. 성능을 극대화하기 위해 언코어 캐시 간 분산을 최소화하고 싶습니다. 이를 위해 kubelet 내부에서 자동으로 처리해주는 기능을 활성화하고 싶습니다.
**Story 2**
- 네트워크/통신 엔지니어로서 지연 시간에 민감한 애플리케이션을 가지고 있습니다. 언코어 캐시 불일치가 이에 영향을 끼치는 요인입니다. 단일 언코어 캐시에 해당하는 CPU로 애플리케이션을 정적으로 할당하여 최대 처리량을 얻고 싶습니다. 또한 다양한 CPU 크리 요구 사항을 가진 정적 애플리케이션이 있습니다. 기본 정적 CPU Manager 클러스터에서 최적의 성능을 보장하기 위해 언코어 캐시 기반 CPU 할당 로직을 자동으로 처리하고 싶습니다.

## Notes/Constrains/Caveats
- [[Uncore Cache]] 용어는 cAdvisor에서 직접 가져온 것
- CPUManagerPolicy{Alpha,Beta} Options 흐름을 따라 feature gate 기능을 사용

## Risk and Mitigations
- 위험 : 기능 활성화/비활성화로 인해 예기치 않은 동작이 발생할 수 있음
	- 해결 : 정적 정책 옵션 플래그를 통해 기능 활성화
- 위험 : 새로운 기능이 기존 기능과 상호작용 문제 발생
	- 해결 : 비정적 정책에는 영향이 없으며, 다른 정적 옵션의 동작을 유지
- 위험 : 일관성 없는 구성으로 인해 예약 문제 발생
	- 해결 : 불일치 시 런타임에 실패가 발생하여 잘못된 정렬이나 비최적 정렬을 방지

## Deisgn Details
Kubelet이 CPU 워크로드에 대해 Uncore Cache를 식별하기 위해, cAdvisor 에서 제공하는 UncoreCacheId가 CPUInfo 및 CPUTopology 구조체에 추가되었습니다.
새로운 CPUManager 정책 옵션인 "prefer-align-cpus-by-uncorecache"가 도입됩니다. 이 옵션이 활성화되면, 기존 스케줄링 기능이 Uncore Cache를 선호하도록 수정됩니다. 할당 프로세스는 먼저 전체 소켓에서 CPU를 할당하려 합니다. 그 다음 NUMA 노드 내에서 CPU를 할당하려 합니다. 마지막으로 이전에 선택된 CPU내에서 각 Unocre Cache에 속한 CPU 부분 집합을 고려합니다. Uncore Cache 정렬이 선호되지만 필수 사항이 아니며, 정렬이 불가능한 경우에도 실패하지 않습니다.
"prefer-align-cpus-by-uncorecache" 알고리즘은 기존 정적 CPU Manager 할당의 기본 패킹동작을 따르되, Uncore Cache 계층 구조를 도입합니다. 즉, 보장된 컨테이너에 필요한 CPU가 NUMA 또는 소켓 크기 이상이면 기존 동작과 도일하게 전체 소켓 또는 NUMA 를 할당합니다. 필요한 CPU에서 할당된 CPU를 뺍니다.
필요한 CPU가 NUMA 노드 내 CPU 수보다 작은 경우, 다음과 같은 알고리즘이 구현됩니다.
1. 각 소켓을 순서대로 검사합니다. 필요한 CPU가 소켓의 사용 가능한 CPU 수보다 작으면 해당 소켓의 CPU를 선택합니다.
2. 선택한 소캣 내에서 각 NUMA를 순서대로 검사합니다. 필요한 CPU가 NUMA의 사용 가능한 CPU 수보다 작으면 해당 NUMA의 CPU 부분 집합을 선택합니다.
3. 선택한 NUMA 내에서 각 Uncore Cache 인덱스를 순서대로 검사합니다.
	- 필요한 CPU가 Uncore Cache의 CPU 수 이상이면 모든 Uncore Cache CPU가 예약되지 않은 경우 전체 Uncore Cache CPU를 할당합니다. 할당된 CPU 수를 필요한 CPU 수에서 뺍니다.
	- 필요한 CPU가 Uncore Cache의 총 CPU수보다 작으면, 숫자 순서대로 각 Uncore Cache를 검사하며 사용한 가능한 CPU가 있는 경우 할당합니다.
4. 필요한 CPU가 Uncore Cache 그룹에 맞지 않지만 노드의 사용 가능한 CPU가 충분한 경우, 숫자 순서대로 코어를 할당합니다.
5. 필요한 CPU를 만족시킬 수 없는 경우 노드에 컨테이너를 예약하지 않습니다.

NUMA 경계가 소켓보다 큰 경우, 위의 스케줄링 정책에서 NUMA 힌트가 제공되면 할당 가능한 CPU 풀은 해당 소켓을 넘어 확장되지 않습니다.

NUMA 경계가 Uncore Cache보다 작은 경우 위의 스케줄링 정책에서 언코어 캐시힌트가 제공되면 할당 가능한 CPU 풀이 해당 NUMA 경계를 넘어 확장되지 않습니다.

이 스케줄링 정책은 기본 압축 논리를 유지하면서 성능을 향상시키기 위해 Uncore Cache 전체의 컨테이너 배포를 최소화합니다. 기본 정적 스케줄링 동작에 대한 Uncore Cache 정렬을 구현하기 위해 처음에는 범위가 좁아집니다. 

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- [[CPU L1,  L2,  L3 Cache]]
- [[L3 Cache Group]]
- [[Kubelet이란]]
- [[Noisy Neighbor Problem]]