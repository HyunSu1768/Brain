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
URL : https://docs.bitnami.com/tutorials/a-deep-dive-into-kubernetes-controllers/

## Controller의 구성요소
- Informer/SharedInformer
- WorkerQueue
## Informer/SharedInformer
- informer/sharedinformer는 kubernetes의 개체의 상태에 대한 변화를 감지하고 WorkerQueue에 이벤트를 전달합니다.
### Informer
여기서 컨트롤러는 개체애 대한 상태를 검색하기 위해 API Server에 요청을 보냅니다.
하지만 API Server에 반복적으로 요청을 보낸다면 서버에대한 부하와 비용이 많이 부과될 수 있습니다. 따라서 client-go에서 제공하는 캐시를 사용합니다. 또한 컨트롤러는 개체에 대해 계속 요청을 보내고싶지 않습니다. 생성 수정 삭제될 때의 이벤트에만 관심이 있습니다. 따라서 client-go에서는 초기 목록을 수행하고 특정 리소스에 대한 감시를 시작하는 ListWatcher 인터페이스를 제공합니다. 현재 Kubernetes에서는 Informer는 많이 사용되지 않고, SharedInformer가 많이 사용됩니다.
### SharedInformer
Informer는 해당 컨트롤러에서만 사용되는 캐시 집합을 생성합니다. Kubernetes는 하나의 리소스에 대해 여러개의 컨트롤러가 존재할 수 있습니다. 이 말은 즉슨 중복된 캐시가 있을 수 있다는 것입니다. SharedInformer는 하나의 컨트롤러에 대한 캐시 집합을 생성하는것이 아닌, 공유될 수 있는 캐시 집합을 생성하여 메모리 오버헤드를 줄입니다. 또한 SharedInformer는 다운스트림 서버의 개수와 상관없이 업스트림 서버에 대한 단일 감시만 생성하여, 업스트림 서버에 대한 부하를 줄여줍니다.

## Worker Queue
SharedInformer는 각 컨트롤러가 어디에 있는지 추적할 수 없습니다. (공유되기 때문에)
따라서 컨트롤러는 자체 대기열 및 재시도 매커니즘이 필요합니다. 컨트롤러는 Worker Queue에서 작업을 순차적으로 처리합니다.

## 정리
SharedInformer는 개체를 감시하며 여러 컨트롤러와 공유합니다. SharedInformer에서 개체 변화 이벤트를 감지한다면 Resource Event Handler 콜백 함수가 작동하여 Work Queue에 해당 개체가 추가되고 Controller는 Work Queue에서 순차적으로 작업을 처리합니다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords : 
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Controller 란?]]