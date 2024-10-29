---
aliases:
  - Envoy
tags:
  - 300-DevOps/360-Envoy
---


---


Source :
Author : 
URL : https://m.blog.naver.com/alice_k106/222000680202

Listener : 어떤 IP, Port 등을 처리할지 결정한다.

Route : Listener로 들어온 요청을 어디로 라우팅할 것인지를 정의한다.

Cluster : 실제 요청이 처리되는 IP 또는 엔드포인트의 묶음을 말한다.

Endpoint : 실제로 접근 가능한 엔드포인트를 말한다. (172.168.0.4, 172.168.0.5) 이러한 엔드포인트가 모여 Cluster가 된다.

### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- 

Related Notes : 
- 