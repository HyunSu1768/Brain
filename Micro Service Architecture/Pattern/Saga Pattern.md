## SAGA 패턴?
* SAGA 패턴이란 마이크로서비스들끼리 이벤트를 주고받으며 만약 특정 마이크로서비스에서 트랜잭션중 실패하게 된다면 이전 마이크로서비스들에게 보상 이벤트를 소싱함으로써 트랜젝션의 원자성을 보장하는 패턴입니다.
<img width="843" alt="Screenshot 2023-08-23 at 9 10 33 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/e5d6d61a-980c-4420-8081-8750693f7865"> <br>
다음 그림은 SAGA 패턴의 이벤트 성공 시 다음과 같은 과정을 거치게 됩니다.
* 하나의 서비스에서 실패없이 로직이 수행됐다면 다음 거쳐야하는 서비스에게 완료 이벤트를 보내게 됩니다.

<img width="852" alt="Screenshot 2023-08-23 at 9 14 59 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/8d106ea4-d82f-4fd9-a59e-95f55f11c70e"> <br>
다음은 로직이 수행되면서 만약 어떠한 것이 실패했을때 실행되는 플로우 입니다.
* 어떠한 한 로직이 실패했다면 이전 서비스에게 실패 이벤트를 보내게 됩니다. 그러면 트랜젝션을 롤백하고 다시 이전 서비스에게 실패 이벤트를 발생시켜 트랜젝션을 롤백해 원자성을 보장할 수 있게 됩니다.
* 이 SAGA패턴의 핵심은 트랜젝션의 관리 주체가 DBMS에 있는것이 아닌 Application 에 있다는 것입니다. 따라서 보상 로직을 모두 구현해야 한다는 불편함이 있습니다.

## SAGA 패턴의 종류
### Choreography based SAGA Pattern
<img width="853" alt="Screenshot 2023-08-23 at 9 26 01 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/15e1e16d-45f3-4765-a52c-1ecea4aefe55"> <br>
* 서비스 내에 Local 트랜젝션을 관리하며 트랜젝션이 종료되게 되면 완료 Event를 발생하게 됩니다. 만약 다음 수행해야할 트랜젝션이 있다면 해당 트랜젝션을 수행해야 하는 App에 이벤트를 보내고, 해당 App은 완료 이벤트를 받고 다음 작업을 진행합니다. 이러한 과정은 Kafka와 같은 Message Queue 를 사용해 비동기처리 합니다.
<img width="862" alt="Screenshot 2023-08-23 at 9 27 20 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/63835acd-0918-4ed8-97eb-dac02d9f5ebd"> <br>
* Choreography Saga Pattern은 각 로직마다 보상 로직이 있기 때문에 Rollback을 수행합니다.
### 장점
* 구성하기 쉽다
### 단점
* 운영자 입장에서 트랜젝션의 현재 상태를 확인하기 어렵습니다.

### Orchestration based SAGA Pattern
<img width="843" alt="Screenshot 2023-08-23 at 9 46 43 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/54bdddee-8903-4e02-96ad-c8ff32c7bf67"> <br>
* Orchestration SAGA Pattern은 트랜젝션을 관리하기 위해 별도의 인스턴스가 존재합니다. App 은 점진적으로 트랜젝션을 수행하며 결과를 Manager에게 전달합니다. 트랜젝션이 종료되게 되면 Manager에게 결과를 전달하고 트랜젝션 과정에서 실패하게 된다면 Manager에게 보상 트랜젝션을 발동하여 일관성을 유지합니다.
<img width="837" alt="Screenshot 2023-08-23 at 9 54 32 AM" src="https://github.com/HyunSu1768/TIL/assets/108796235/a644e3c7-53f0-4470-bb9e-3b29373a709e"> <br>
이러한 Orchestration SAGA Pattern은 트랜젝션을 Manager가 관리하기 때문에 분산 트랜젝션의 중앙 집중화가 이루어집니다.

### 장점
* 서비스간 복잡성이 줄어들고 구현 및 테스트가 쉽습니다.
* 트랜젝션의 현재 상태를 Manager가 알고 있으므로 롤백하기 쉽습니다.

### 단점
* 관리를 해야하는 Orchestrator 서비스가 추가되어야하기 때문에 인프라 구현이 복잡해 집니다.

## 정리
* MSA에서는 각 서비스가 각각의 단일 데이터베이스를 가지고 있기 때문에 분산 트랜젝션을 관리하기 힘듭니다. 따라서 SAGA Pattern을 사용하여 이러한 분산 트랜젝션 문제를 해결할 수 있습니다.
