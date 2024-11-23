---
aliases:
  - Kubernetes
tags:
  - 문헌메모
  - 완료
---


---


Source : /pkg/kubelet/pod/mirror_client 
Author : 
URL :

```
type basicMirrorClient struct {  
    apiserverClient clientset.Interface  
    nodeGetter      nodeGetter  
    nodeName        string  
}
```

```
func (mc *basicMirrorClient) CreateMirrorPod(pod *v1.Pod) error {
...
}
```

```
func (mc *basicMirrorClient) DeleteMirrorPod(podFullName string, uid *types.UID) (bool, error) {
...
}
```

```
func (mc *basicMirrorClient) getNodeUID() (types.UID, error) {

}
```

Mirror Client는 kubelet의 구성요소로 kubelet은 노드에 배치된 Pod를 감시하며 api-server에 상태를 보고해야 하는 역할을 가지고 있는데, api-server가 관리하지 않는 static pod의 경우에는 mirror client가 Mirror Pod를 생성하여 api-server에 상태를 보고한다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Kubernetes]]

Related Notes : 
- [[Kubelet이란]]