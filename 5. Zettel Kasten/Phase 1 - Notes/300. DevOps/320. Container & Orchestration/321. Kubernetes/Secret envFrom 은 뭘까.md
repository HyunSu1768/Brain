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
URL : https://kubernetes.io/ko/docs/concepts/configuration/secret/#%EC%8B%9C%ED%81%AC%EB%A6%BF%EC%9D%84-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%ED%98%95%ED%83%9C%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0

## envFrom
- 시크릿의 모든 데이터를 컨테이너의 환경변수로 사용한다.
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-test-pod
spec:
  containers:
    - name: test-container
      image: registry.k8s.io/busybox
      command: [ "/bin/sh", "-c", "env" ]
      envFrom:
      - secretRef:
          name: mysecret
  restartPolicy: Never
```

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- 