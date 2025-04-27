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
URL :

## OwnerReferences
OwnerReferences 필드는 metadata 안에 존재하는 필드이다. 
OwnerReferences 는 리소스 간의 소유를 나타내는 필드로 예시는 다음과 같다.

```yaml
ownerReferences:
- apiVersion: apps/v1
  kind: ReplicaSet
  name: my-replicaset
  uid: "dcd067d8-1d2a-11e9-a4a3-42010a8000aa"
  controller: true
  blockOwnerDeletion: true
```
다음은 ReplicaSet에 의해 생성된 Pod의 ownerReferences 필드이다.
kind 에 어떤 리소스에 의해 생성되어있는지 확인할 수 있고, 이는 리소스를 삭제할때 주소 쓰인다.
만약 ReplicaSet이 삭제되면 GC Controller는 onwerReferences 필드를 확인하고 ReplicaSet이 삭제되었기 때문에 ReplicaSet에 의해 생성된 파드를 삭제한다. cascade delete 이다.

## Finalizer
만약 onwerReferences 로 인해 삭제되어야 하는것이 삭제되지 않는 경우는 무엇일까?
바로 finalizer이다. finalizer 는 리소스가 삭제되기 전에 작동해야 하는 행위를 설정하고, 해당 행위가 작동이 완료되기 전까지는 삭제되지 않는다. 예를들면 PVC를 보호하기 위해 PVC를 임의로 삭제하기 전까지는 리소스가 삭제되지 않는다. 이런 경우 해당 리소스의 finalizer 필드를 제거해서 리소스를 삭제할 수 있다.
```yaml
metadata:
  finalizers:
    - kubernetes.io/pvc-protection
```


### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- 