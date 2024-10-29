---
aliases:
  - Containerd
tags:
  - 문헌메모
  - 완료
---


---


Source : containerd/internal/cri/server/version.go
Author : 
URL : 

## Version 메서드
```
const (  
    containerName = "containerd"  
    // kubeAPIVersion is the api version of kubernetes.    // TODO(random-liu): Change this to actual CRI version.  
    kubeAPIVersion = "0.1.0"  
)

func (c *criService) Version(ctx context.Context, r *runtime.VersionRequest) (*runtime.VersionResponse, error) {  
    return &runtime.VersionResponse{  
       Version:           kubeAPIVersion,  
       RuntimeName:       containerName,  
       RuntimeVersion:    version.Version,  
       RuntimeApiVersion: constants.CRIVersion,  
    }, nil  
}
```
이와 같이 미리 정의해둔 상수를 통해 간단하게 kubernetes에서 사용하고 있는 Container Runtime의 버전 정보를 반환합니다.
### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Containerd]]
- [[gRPC란?]]

Related Notes : 
- [[Container Runtime Interface란?]]