# Control Plane
![[Pasted image 20231029223659.png]]
- [Kubernetes](./Kubernetes.md)에 배포되는 Container를 관리하기 위한 구성요소들은 Control Plane이라고 함
- [Master Node](./Master%20Node.md) 에 배포되며 minion node의 [Kubelet](./Kubelet.md) 과 통신하면서 Container를 관리한다.

## Control Plane의 구성요소
- [etcd](./etcd.md)
- [[API Server]](kube-api-server)
- [Controller Manager](./Controller%20Manager.md)
- [Scheduler](./Scheduler.md)
