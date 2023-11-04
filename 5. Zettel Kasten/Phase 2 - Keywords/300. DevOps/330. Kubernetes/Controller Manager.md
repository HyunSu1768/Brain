# Controller Manager
- 클러스터 내에서 실행되는 여러 개의 컨트롤러를 통합 관리하는 프로세스
- 컨트롤러는 클러스터 내의 리소스 상태를 검사한다
- 사용자가 정의한 상태를 유지하기 위해 조치를 취한다.

# 주요 컨트롤러
- [Replication Controller](Replication%20Controller.md)
- [ReplicaSet](ReplicaSet.md)
- [Deployment](Deployment.md)
- [StatefulSet](StatefulSet.md)

## Kube Controller Manager 의 구성
- 마스터 노드의 일부로 동작한다.
- 쿠버네티스 클러스터 생성 시 자동으로 마스터노드에 배포된다.
- 기본적으로 필요한 컨트롤러는 모두 활성화되며 필요시에 비활성화, 추가할 수 있다.

## Kube Controller Manager의 중요성
- 클러스터의 안정성과 가용성을 유지하는 데 중요한 역할을 한다
- 다양한 컨트롤러를 통해 파드의 복제, 롤링 업데이트, 상태 유지 등 다양한 기능을 수행하여 클러스터의 관리를 간소화 한다.
