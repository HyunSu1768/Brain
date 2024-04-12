---
aliases: 
tags:
---


---


Source :
Author : 
URL : 

## gRPC란?
- google에서 개발한 RPC 프레임워크
- protocol buffer 기반 통신방식으로 기존 XML, json 방식과 달리 text 기반이 아닌 바이너리 코드로 작성되어 통신이 매우 빠르며, 오버헤드가 적음
- 

## RPC란?
- Remote Procedure Call의 약자로 별도의 통신 코드를 작성하지 않고, 다른 공간에서 원하는 함수나 프로시저를 직접적으로 실행할 수 있도록 함
- RPC는 원격에 있는 애플리케이션의 메서드를 로컬 메서드처럼 사용할 수 있어, HTTP 통신보다 빠른 성능을 자랑함.

## 기존 RPC와 gRPC의 차이점
- 기존 RPC는 text기반으로 통신하여 오버헤드가 커 비효율적임, gRPC는 protocl buffer 기반 바이너리 파일로 컴파일되기 때문에 통신이 빠름. 또한 stream으로 여러 요청, 또는 여러 응답을 받을 수 있으며 비동기 요청을 보낼 수 있음

## gRPC의 단점
- 바이너리 파일로 컴파일되기 때문에 사람이 요청을 읽을 수 없음
- 만약 미리 정의해놓은 객체 모델을 수정한다면 해당 rpc를 사용하는 클라이언트, 서버를 모두 수정해야 함

### Link of Thoughts
Area : #500-Network 

Keywords :
- 

Related Notes : 
- [[Container Runtime Interface란?]]