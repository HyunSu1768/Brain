---
aliases:
  - Network
tags:
  - 완료
  - 문헌메모
---


---


Source :
Author : 
URL :

### API URI 고민
* 리소스의 의미는?
  * 회원을 등록하고 수정하고 조회하는게 리소스가 아니다
  * 예) 미네랄을 캐라 -> 미네랄이 리소스이다.
  * 회원이라는 개념 자체가 바로 리소스이다.

* 리소스를 어떻게 식별하는게 좋을까
  * 회원을 등록하고 수정하고 조회하는 것을 모두 배제한다.

* 이러면 나머지 수정,조회같은 문제점이 발생한다. 아래에서 설명하는것으로 해결할 수 있다.

### HTTP METHOD
* 메서드의 종류
  * GET: 리소스 조회
    * 리소스 조회
    * 서버에 전달하고 싶은 데이터는 query를 통해서 전달
    * 메시지 바디를 사용해서 데이터를 전달할 수 있지만, 지원하지 않는 곳이 많아서 권장하지 않는 방법이다.
  * POST: 요청 데이터 처리, 주로 등록에 이용
    * 요청 데이터를 처리한다.
    * 메시지 바디를 통해 서버로 요청 데이터를 전달한다.
    * 서버는 요청 데이터를 처리한다.
      * 메시지 바디를 통해 들어온 데이터를 처리하는 모든 기능을 수행한다.
    * 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용된다.
  * PUT: 리소스를 대체, 해당 리소스가 없으면 생성
    * 리소스를 대체
  * PATCH: 리소스 부분 변경
    * 리소스 부분 변경
  * DELETE: 리소스 삭제


### Link of Thoughts
Area : #500-Network 

Keywords :
- 

Related Notes : 
- 