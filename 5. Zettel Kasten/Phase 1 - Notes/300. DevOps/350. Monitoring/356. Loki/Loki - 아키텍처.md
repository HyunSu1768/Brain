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

## Loki의 아키텍처
![[Pasted image 20250829104440.png]]

### Write Path : Distributor, Ingester
![[Pasted image 20250829104710.png]]
### Distributor
클라이언트로부터 받은 스트림을 처리하여 Ingester 로 전달하는 역할을 한다.

주요 특징
- 유효성 검사 : 들어온 데이터가 Grafana LGTM 사양에 부합하는지 확인한다.
- 전처리 : 스트림의 레이블을 정렬하는 과정으로, 이를 통해 Loki는 데이터를 효율적으로 캐시하고 해시할 수 있다.
- 속도 제한 : 테넌트별 최대 전송률을 설정하여, 들어오는 로그의 전송률을 제어할 수 있습니다. 이는 시스템의 안정성을 유지하는 데 중요한 역할을 한다.
	- replication factor가 3이라면 Ingester 내에 3개의 복제본을 생성하도록 3개의 스트림을 전달합니다.
- 해싱 : 일관된 해싱을 사용해 특정 스트림이 전달될 Ingester 인스턴스를 결정한다.
- 쿼럼 일관성 (Quorum Consistency) : 최소 절반 이상의 Ingester로부터 응답을 받기 전까지는 클라이언트에게 응답을 보류한다.

### Ingester
Ingester는 로그 데이터를 저장소 백엔드에 저장하는 역할을 한다.

주요 기능 및 특징
- 청크 처리 : 로그 스트림은 메모리 내에서 여러 '청크' 집합으로 관리되며, 설정 가능한 주기에 따라 저장소 백엔드로 플러시한다.
- 데이터 복제 : 갑작스러운 종료나 충돌로 인해 플러시되지 않은 데이터 손실을 방지하기 위해, 여러 Ingester에 복제한다. (replication_factor)
- d

로그 스트림이 청크에 저장되는 과정
1. distributor는 스트림에 대한 요청을 받는다.
2. 각 스트림은 해시 링을 사용해서 해시된다.
3. distributor는 각 스트림을 적절한 ingesters에 해당 복제본을 보낸다. (rf가 복수일 경우 복제해서)
4. 각 ingesters는 스트림 데이터에 대해 청크를 생성하거나 기존 청크에 추가한다.
5. distributor는 성공 코드로 응답한다.


## Read Path : Query Frontend, Querier
![[Pasted image 20250829163417.png]]

### Query Frontend (optional service)
Querier를 보조하는 역할로 읽기 경로의 성능을 향상시키는 모듈이다.
- 큐잉 : 큰 쿼리로 인한 메모리 부족 문제를 방지하고, 공정한 스케줄링이 가능하게 한다.
- 분할 : 큰 쿼리를 여러 작은 쿼리로 분할하여 Querier의 메모리 부족 문제를 예방한다.
- 캐싱 : 쿼리 결과를 캐시하여 후속 쿼리에서 사용한다. 쿼리 수행 시간을 단축시키고 전반적인 시스템 성능을 향상시키는데 도움이 된다.

### Querier
LogQL 쿼리 언어를 사용하여 로그 데이터에 대한 쿼리를 처리한다.
- 인메모리 데이터 및 장기 저장소 쿼리 : Ingester에서 현재 메모리에 있는 데이터를 쿼리한 다음, 같은 쿼리를 장기 저장소에 대해서도 실행한다.
- 중복 제거 : 복제로 인해 중복된 데이터가 발생할 수 있는데, Querier가 dedup을 하여 중복 데이터를 방지한다.

Read Path에서 로그 스트림이 읽어지는 과정:
1. querier 는 데이터에 대한 요청을 받는다.
2. querier는 인메모리 데이터에 대한 쿼리를 모든 ingester에게 요청한다.
3. ingesters는 읽기 요청을 수신하고 쿼리와 일치하는 데이터가 있는 경우 반환한다.
4. querier는 데이터를 반환한 ingesters가 없는 경우 백업 저장소에서 데이터를 느리게 로드하고 이에 대해 쿼리를 실행한다.
5. querier는 수신된 모든 데이터를 반복하고 중복을 제거하여 최종 데이터 세트를 반환한다.


## Consistence Hash Rings
distributor에서 스트림이 일정한 Ingester로 전송될 수 있도록 하는 기능.
스트림을 일정한 Ingester에 저장했을 경우 이점은 다음과 같음. read 과정에서 스트림에 대해 저장되어있는 곳을 O(1) 수준으로 검색할 수 있기 때문에 검색 효율적이며, 일관성있음


### Link of Thoughts
Area : #300-DevOps/350-Monitoring 

Keywords :
- [[Loki]]

Related Notes : 
- [[Loki - 뛰어난 확장성]]