---
aliases:
  - Kubernetes
tags:
  - 의견메모
  - 완료
---
### 1.
Notes : Controller에 대해 알아보기
- [[Controller 란?]]

### 2.
Notes : Controller의 구성요소와 작동방식
- [[5. Zettel Kasten/Phase 1 - Notes/300. DevOps/320. Container & Orchestration/321. Kubernetes/Controller의 구성요소|Controller의 구성요소]]


### 3.
Notes :
- 

### Link of thoughts
Area : #300-DevOps/320-Container-Orchestration 
Keyword : [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes :
- [[Controller 란?]]
- [[Controller의 구성요소]]

Same Opinion :
-

Opposite Opinion :
-

Question :
- Kubernetes Controller가 감시하는 리소스들이 많아진다면 그에대한 부하는 늘어나지 않을까?

Answer :
- Kubernetes Controller는 SharedInformer, Work Queue를 가지고 있으며, SharedInformer는 하나의 객체의 이벤트를 캐시한 데이터를 공유함으로써 중복되는 캐시를 줄여 부하를 줄이고, 컨트롤러가 직접적으로 API Server에 요청을 보낼 필요를 제거함으로써 API Server의 부하를 줄였습니다. Work Queue는 여러 컨트롤러가 비동기적으로 작업을 처리할 수 있도록 하여 처리 성능을 높였습니다. 이 구조들은 높은 확장성과 안정성을 제공하며 대규모 클러스터 환경에서도 뛰어난 성능을 발휘할 수 있도록 합니다. 또한 SharedInformer, Work Queue는 개발자가 Controller를 개발할 때 성능 문제로 고민하는 일을 최소화 합니다.

Claim :
- 