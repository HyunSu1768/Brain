---
aliases: 
tags:
---


---


Source : kubernetes
Author : 
URL : 

## RemoteRuntimeService란?
- 내부 API, RuntimeService의 gRPC 구현체이다.

## RemoteRuntimeService의 구조
```
type remoteRuntimeService struct {  
    timeout       time.Duration  
    runtimeClient runtimeapi.RuntimeServiceClient  
    // Cache last per-container error message to reduce log spam  
    logReduction *logreduction.LogReduction  
}
```
- timeout, runtimeClient, logReduction으로 구성되어 있다.


## RemoteRuntimeService의 쓰임
kubelet을 실행하기 전에 PreInitRuntimeService라는 함수에서 remote_runtime.go 파일에 정의되어 있는 NewRemoteRuntimeService 함수를 호출해 kubelet 구현에 사용됨
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- [[Container Runtime Interface란?]]
- [[RuntimeService란?]]
