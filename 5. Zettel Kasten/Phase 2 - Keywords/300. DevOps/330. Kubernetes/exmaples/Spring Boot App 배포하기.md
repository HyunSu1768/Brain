# Kubernetes Deployment, Service

오늘은 Spring boot app 을 kuberentes로 배포하고 복제본을 만들어 load balancing 하는것 까지 해보겠다.

먼저 준비사항은 Spring boot app Docker Image와 kuberentes가 설치되어 있으면된다.

내 Spring boot app 은 간단하게 HelloWorld 를 출력하고 로드밸런싱이 되는걸 확인하기 위해 Hostname을 출력하도록 했다.

<img width="445" alt="Screenshot 2023-09-18 at 12 10 29 PM" src="https://github.com/HyunSu1768/TIL/assets/108796235/0f5a5e59-3bf4-4d03-a167-1df492c7f046">


그리고 docker build를 하고 docker hub에 올려준다.

그리고 이제 kubernetes yaml을 작성하면 된다.

그 전에 약간의 개념을 보고 가자

## ReplicaSet, Deployment, Service(Load Balancer)란?
### ReplicaSet
ReplicaSet은 Deployment에서 가장 중요한 개념입니다.
Replication Controller 의 새로운 버전으로 Label Selector를 통해 노드 상의 Pod를 생성/복제/삭제 등의 라이프 사이클을 관리합니다.

1. 지정한 Replica의 수 만큼 Pod의 개수를 유지합니다.
2. Label Selector 를 통해 Pod를 찾습니다.

### Deployment
Deployment는 Kubernetes에서 어플리케이션을 관리한는 Controller입니다.
Kubernetes에서 최소 단위인 Pod의 기준 스펙을 정의합니다.

Kubernetes 에서는 각 오브젝트를 독립적으로 생성하기 보단 Deployment를 사용해서 생성하기를 권장하고 있습니다.
1. Pod의 Scale in / out 기준을 정의합니다.
2. Pod의 배포되고 UPDATE되는 모든 버전을 추적할 수 있습니다.
3. 배포된 Pod에 대해서 rollback을 수행할 수 있습니다.

즉 Deployment는 ReplicaSet + Pod + History라고 할 수 있습니다.

### Service
오늘은 Service 중에서도 LoadBalancer 서비스를 사용할 것이다.

LoadBalancer를 사용하면 외부에서 접속 가능하게 만들어주고 자신만의 고유한 IP주소를 가지며 모든 서비스로 리다이렉트 합니다.
또한 여러개의 Pod가 있다면 트래픽을 분산시킵니다.

## helloworld-deployment.yaml, helloworld-service.yaml 작성
Spring boot app을 배포하기 위해 deployment와 service를 정의합니다

selector는 pod를 어떻게 식별할지 정의하고 있습니다.
template에 적혀있는 내용은 말 그대로 Pod를 정의하는 템플릿이며 label을 helloworld-app으로 함으로서 label selector가 helloworld-app을 찾아 pod를 관리합니다.
replicas를 3으로 해서 파드를 3개 복제합니다.
그리고 containers에 컨테이너 이미지, 이름, 포트, 프로토콜, 그리고 리소스에 대한 limit을 설정할 수 있습니다.
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: helloworld-deployment
spec:
  selector:
    matchLabels:
      app: helloworld-app
  replicas: 3
  template:
    metadata:
      labels:
        app: helloworld-app
    spec:
      containers:
        - name: helloworld-container
          image: hyunsu1768/helloworld:latest
          imagePullPolicy: Always
          ports:
            - containerPort: 8080
              protocol: TCP
          resources:
            requests:
              cpu: 500m
              memory: 1000Mi
```

`kubectl apply -f helloworld-deployment.yaml`
를 사용해 deployment를 실행할 수 있습니다.

우리는 지금 Deployment를 정의하여 pod를 생성하였지만 외부에서 pod에 접근하지 못하는 상태입니다. 따라서 우리는 LoadBalancer Service를 정의하여 외부에서 pod에 접근할 수 있도록 합니다.

다음은 helloworld-service.yaml 입니다. 
```
apiVersion: v1
kind: Service
metadata:
  name: helloworld-service
spec:
  type: LoadBalancer
  ports:
    - name: port1
      port: 8080
      protocol: TCP
      targetPort: 8080
  selector:
    app: helloworld-app
```

kind를 Service로 정의해 줍니다.

selector 를 사용해서 파드의 라벨이름을 적어줍니다. 또한 ports를 정의해 줍니다.

`kubectl apply -f helloworld-service.yaml` 을 사용해서 service를 실행할 수 있습니다.

`kubectl get pods` 를 사용해서 파드의 목록을 볼 수 있습니다.
<img width="554" alt="Screenshot 2023-09-18 at 12 35 07 PM" src="https://github.com/HyunSu1768/TIL/assets/108796235/c29d5adb-5e46-4f7f-8532-cc6d87140b8e">
replicas를 3으로 설정했기 때문에 같은 파드가3 개 실행되는 것을 볼 수 있습니다.

또한 pod에 대한 세부적인 항목을 보고싶다면
`kubectl describe pod < 파드이름 >` 을 통해 볼 수 있습니다.
<img width="545" alt="Screenshot 2023-09-18 at 12 36 14 PM" src="https://github.com/HyunSu1768/TIL/assets/108796235/b28a24d1-fbc8-464f-971c-90ddb9d2aa33">



이제 한번 확인해볼 시간입니다.

지금 minikube라는 테스트 클러스터를 사용하고 있는데 minkube에서는 loadbalancer의 ip를 제공하기 않기 때문에
`minikube service helloworld-service` 를 사용해 정상적으로 작동되게 할 수 있습니다.

<img width="451" alt="Screenshot 2023-09-18 at 12 37 52 PM" src="https://github.com/HyunSu1768/TIL/assets/108796235/ceb31d80-d64e-483c-8746-e074d0536581">

이렇게 접속이 가능합니다.

우리는 3개의 복제본을 만들고 loadbalancer를 정의해주었기 때문에 트래픽을 다시 보내면 다른 pod에서 응답할 수 있습니다.
<img width="441" alt="Screenshot 2023-09-18 at 12 38 35 PM" src="https://github.com/HyunSu1768/TIL/assets/108796235/1091e9c1-338d-413f-8eea-2422beb92559">
이런식으로 !
