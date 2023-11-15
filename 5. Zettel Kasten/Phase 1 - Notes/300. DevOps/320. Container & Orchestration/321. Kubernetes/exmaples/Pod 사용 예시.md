---
aliases: 
tags:
---


---


Source :
Author : 
URL :

다음과 같이 간단하게 작성될 수 있습니다.

```yaml
apiVersion: v1
kind: Pod
metadata:
name: nginx
spec:
containers:
 - name: nginx
   image: nginx
   ports:
   containerPort: 80
```

- image는 도커 이미지의 이름
- containerPort는 nginx 컨테이너에서 노출하는 포트를 의미합니다. 그래서 우리는 pod의 IP를 가지고 nginx 서버에 연결할 수 있습니다.
- 기본적으로 이미지에 정의된 포트로 실행됩니다.

이제 이 파드에 Log truncator container를 추가해 봅시다. 

이를 위해 공유할 수 있는 볼륨에 로그를 기록하는 nginx가 필요합니다. 이 볼륨을 emptyDir이라고 정의하겠습니다. Pod가 시작 될 때 빈 디렉터리로 시작되고 파드가 꺼지면 없어지지만, 파드를 다시 시작하면 유지됩니다.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
      - containerPort: 80
      volumeMounts:
      - mountPath: /var/log/nginx
        name: nginx-logs
    - name: log-truncator
      image: busybox
      command:
      - /bin/sh
      args: [ -c, 'while true; do cat /dev/null > /logdir/access.log; sleep 10; done' ]
      volumeMounts:
        - mountPath: /logdir-hyunsu
          name: nginx-logs
  volumes:
  - name: nginx-logs
    emptyDir: {}
```

nginx-logs 라는 이름을 가진 emptyDir 볼륨을 추가했습니다.

nginx는 /var/log/nginx 에 로그를 작성합니다. 그래서 우리는 nginx컨테이너의 해당 위치에 해당하는 볼륨을 마운트합니다. 

우리는 busybox를 사용합니다. busybox는 linux에서 쓰이는 간단한 CLI입니다. busybox는 우리가 필요한 로그 수집기 등 모든것을 제공합니다.

log-truncator 컨테이너 안에서는 /logdir-hyunsu에 마운트하여 10초마다 로그파일을 작성하는 쉘 루프를 실행하도록 하였습니다.

## 파드를 실행해 봅시다!

```yaml
kubectl apply -f nginx.yaml
```

을 사용해 파드를 실행시킵니다.

그리고 외부에서 접근할 수 있도록 포트포워딩 해줍니다.

```yaml
kubectl port-forward 8080:80
```

이렇게 하면 [localhost:8080](http://localhost:8080) 을 사용해서 nginx에 접속할 수 있습니다.

![Screenshot 2023-09-19 at 7 29 25 PM](https://github.com/HyunSu1768/TIL/assets/108796235/9ec1f00a-b12a-44f2-9bc0-220a76cfd0fa)

우리는 이제 log-truncator 에 접속해 /logdir-hyunsu에 로그가 있는지 확인하면 됩니다.

log-truncator에 접속해 봅시다.

```yaml
kubectl exec -it nginx -c log-truncator -- /bin/sh
```

이렇게 접속한 뒤 ls 를 해보면

![Screenshot 2023-09-19 at 7 29 44 PM](https://github.com/HyunSu1768/TIL/assets/108796235/2f5af7b4-45bf-4af3-a1c3-475af718c7b7)


logdir-hyunsu 라는 디렉토리가 있는것을 확인할 수 있고

들어가서 cat error.log 를 확인해 보면

![Screenshot 2023-09-19 at 7 29 59 PM](https://github.com/HyunSu1768/TIL/assets/108796235/d2d1ed30-21ce-41a9-9953-827af3604127)


이렇게 잘 보이는것을 확인할 수 있다.!!

우리는 이렇게 실습을 하면서 파드 안에서는 볼륨을 공유할 수 있다는 사실을 알 수 있다!!


### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- 

Related Notes : 
- [[Pod란]]