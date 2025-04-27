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
먼저 GoCD를 사용하던 환경에서 빌드가 실행되면 Elastic Agent가 Pod 형태로 생성되게 됩니다. 해당 Pod에 EBS에 연결되어 있는 PVC를 연결해 줍니다. Dockerfile 에서는 빌드 명령어를 RUN 하는 부분에 mount=type=cache 옵션을 사용해서 명령어에서 생성된 캐시를 저장하고 나중에 해당 명령어를 실행할때 캐시를 사용하여 빌드를 하도록 합니다. 이를 통해 빌드 속도를 최대 80% 를 감소시켰습니다. 하지만 EBS는 동적으로 용량이 늘어나지 않기 때문에 주기적으로 EBS크기를 늘려주거나 오래된 cache 를 정리해줘야만 했습니다. 또한 서비스가 많아지면 많아질수록 EBS비용이 눈에 띄게 증가하였기 때문에 처음 도입할 때는 생각하지 못했던 문제가 발생하였습니다.

### Link of Thoughts
Area : #1110-Interview 

Keywords :
- 

Related Notes : 
- 