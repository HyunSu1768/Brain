---
aliases:
  - Containerd
tags:
  - 문헌메모
  - 완료
---


---


Source : containerd/internal/cri/server/sandbox_run.go 
Author : 
URL : 

## Network Namespace 생성
```go
func (c *criService) RunPodSandbox(ctx context.Context, r *runtime.RunPodSandboxRequest) (_ *runtime.RunPodSandboxResponse, retErr error)
```
PodSandbox는 완벽하게 외부환경으로부터 격리해야 하기 때문에 네트워크 통신 부분도 분리합니다.
```go
if !hostNetwork(config) && !userNsEnabled {
...
	var netnsMountDir = "/var/run/netns"  
	if c.config.NetNSMountsUnderStateDir {  
	    netnsMountDir = filepath.Join(c.config.StateDir, "netns")  
	}  
	sandbox.NetNS, err = netns.NewNetNS(netnsMountDir)
...
}
```
k8s의 pod spec에서 hostNetwork를 설정할 수 있는데 해당 옵션이 비활성화 되어 있는 경우에는 네트워크를 격리하기 위해 network namespace 를 생성합니다.

## 눈으로 확인하기
눈으로 확인해 보기 위해 k8s node 에 접속하여 /var/run/netns 에 존재하는 디렉토리 개수를 확인합니다.
```
[root@ip-10-0-7-118 netns]# ls
cni-16b5e306-6af6-d2c7-a377-87f43a19005a  cni-cc4bf0ba-8ce8-f3ff-0535-a2fa4f0c525f
cni-87916229-d99a-4888-5727-22817a361945  cni-e0b084d5-9fd5-4dbc-64d5-c201fcfc153c
[root@ip-10-0-7-118 netns]# ls | wc -l
4
```

Network Namespace 가 4개로 나뉘어져 있고


```
k get pod -o wide -A | grep ip-10-0-7-118.ap-northeast-2.compute.internal | wc -l
       6
```
실제로 해당 노드에서의 파드 개수는 6개입니다. 아까 말했던 것처럼 hostNetork가 활성화 되어있는 경우에는 network namespace를 생성하지 않기 때문에 kube-proxy와 aws-ebs-node 파드를 제외하면 4개가 맞습니다.

그러면 옛날에 생성되었던 network namespace는 어떻게 될까요?

```go
defer func() {  
    // Remove the network namespace only if all the resource cleanup is done  
    if retErr != nil && cleanupErr == nil {  
       if cleanupErr = sandbox.NetNS.Remove(); cleanupErr != nil {  
          log.G(ctx).WithError(cleanupErr).Errorf("Failed to remove network namespace %s for sandbox %q", sandbox.NetNSPath, id)  
          return  
       }  
       sandbox.NetNSPath = ""  
    }  
}()
```
그 부분은 containerd 코드에서 파드가 종료되면 생성했던 network namespace를 삭제하도록 작성되었기 때문에 삭제됩니다.
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Containerd]]

Related Notes : 
- [[Container Runtime Interface란?]]
- [[Sandbox란?]]
- [[Namespace란?]]