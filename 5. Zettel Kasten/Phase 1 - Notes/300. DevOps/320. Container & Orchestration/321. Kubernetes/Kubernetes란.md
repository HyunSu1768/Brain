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

# Kubernetes
- 대규모 클러스터 환경에서 컨테이너화된 애플리케이션을 자동으로 배포, 확장, 관리하는 데 필요한 여러가지 요소들을 자동화하는 오픈소스 플랫폼
- 사용자 부하에 따라 자동으로 애플리케이션과 서버의 규모를 확장, 축소할 수 있고 네트워크,스토리지, 모니터링 등 시스템 운영에 필수적인 여러 컴포넌트를 편리하게 구축, 관리할 수 있다
- 소스코드를 기반으로 클러스터를 관리한다.
```
애플리케이션 볼륨 설정
	volumeMounts:
	- name: data-vol
	- mountPath: /data
volumes:
- name: data-vol
  persistentVolumeClaim:
    claimName: default01-pvc
```

이렇게 소스코드로 관리함으로써 개발팀, 데브옵스팀, 보안팀 등 모든 이해관계자가 사전에 충분히 검토할 수 있다

## 의도한 상태를 유지
- 쿠버네티스는 의도한 상태를 기준으로 관리한다.
- 쿠버네티스 컨트롤러가 자동으로 끊임없이 확인한다. (Go언어의 'watch'모듈을 사용)
- 차이점을 발견하면 현재 상태를 자동으로 처음에 의도한 상태로 변경(self-healing)

## 클라우드
- 클라우드 환경의 표준 운영체제가 되어가고 있음
- AWS, Microsoft, Google, RedHat 등 수많은 벤더들이 쿠버네티스를 기반으로 다양한 솔루션을 제공하고 있다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration  

Keywords :
- [[5. Zettel Kasten/Phase 2 - Keywords/Kubernetes|Kubernetes]]

Related Notes : 
- 