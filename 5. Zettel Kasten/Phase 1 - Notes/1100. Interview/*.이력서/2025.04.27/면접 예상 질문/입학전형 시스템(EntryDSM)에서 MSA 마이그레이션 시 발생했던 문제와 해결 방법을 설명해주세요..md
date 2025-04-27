---
aliases:
  - Interview
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Answer
하나의 마이크로서비스에서 Kafka Topic을 Produce, Consume 하는 로직이 있었습니다. Consume을 하는 로직은 Produce를 하기전에 데이터 변경 후에 작동되어야 하는 로직이었지만 모종의 이유로 Consume 하는 로직에서 데이터가 변경되지 않은 상태에서 로직이 실행되어 올바른 결과가 나오지 않았습니다. 따라서 APM의 Trace를 확인하여 Topic 발행 시점, 소비 시점과 Transaction이 commit 되는 시점을 파악하였습니다. 문제는 Transaction이 consume 후에 로직이 완료될 때 commit 되어 올바른 결과가 나오지 않았습니다. 따라서 Spring Framework의 TransactionSynchronizationManager을 사용하여 commit 후에 Topic을 발행하도록 코드를 작성하여 문제를 해결하였습니다.

### Link of Thoughts
Area : #Interview 

Keywords :
- 

Related Notes : 
- 