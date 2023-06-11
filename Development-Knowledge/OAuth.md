### OAuth 란?
#### 정의
> OAuth는 인터넷 사용자들이 비밀번호를 제공하지 않고 다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 공통적인 수단으로서 사용되는, 접근 위임을 위한 개방형 표준이다.
OAuth 2.0 은 1.0에서 알려진 보안 문제 등을 개선한 버전이다.

#
### OAuth 구성 요소
* Resource Owner
  * 웹 서비스를 이용하려는 유저, 자원을 소유하는 자, 사용자
  * 'Resource"는 개인정보이다.
  * 개인정보의 주인

* Client
  * 자사 또는 개인이 만든 `애플리케이션 서버` 
  * 클라이언트 라는 이름은 client가 Resource server에게 필요한 자원을 요청하고 응답하는 관계이기 때문이다.

* Authorization Server
  * 권한을 부여(인증에 사용할 아이템을 제공)해주는 서버이다.

* Resource Server
  * 사용자의 개인정보를 가지고있는 애플리케이션 (Google, Facebook, Naver, Kakao 등) 회사 서버
  * Client는 Token을 이 서버로 넘겨 개인정보를 응답 받을 수 있다.

* Access Token
  * 자원에 대한 접근 권한을 Resource Owner가 인가하였음을 나타내는 자격증명

* Refresh Token
  * Client는 Authorization Server로 부터 access token과 refresh token 을 함께 부여 받는다.
  * access token은 보안상 만료기간이 짧기 때문에 얼마 지나지 않아 만료되면 사용자는 로그인을 다시 시도해야 한다.
  * 그러나 refresh token이 있다면 access token이 만료될 때 refresh token을 통해 access token을 재발급 받아 다시 로그인 하지 않아도 되게 한다.
#

<img width="1098" alt="스크린샷 2023-06-11 오후 1 54 34" src="https://github.com/HyunSu1768/TIL/assets/108796235/d8e69e56-c34a-4e98-ac14-f1875bd36aa6">

직접 사용자가 로그인 하는것이 아닌, 소셜 미디어로 로그인을 할 경우,

client(개인 서비스)는 Resource Owner(사용자)를 대신해 로그인 하는데, 이때 필요한 정보를 Resource Server에서 얻어 서로 비교해 유효성을 판단한다.

client가 유저의 (로그인)정보/자원(resource)을 Resouorcce Server에 요청해 대신 로그인 하는 것이다.

이를 위해서는 client는 다음 단계들을 가진다.
* Resource Owner로 부터 동의(허용)
* Resource Server로 부터 client 신원확인

### Resource Owner의 입장
> 자신의 정보를 대신 사용하기 때문에 나쁜 마음을 가지면 개인정보를 마구잡이로 악용할 수 있을 수도 있기 때문이다.
> 그러므로 client는 Resource Owner의 동의를 구해야 한다.

### Resource Server(kakao) 입장
> 다른 사람의 일을 대신 해주는 사람이 정말 그 사람일지 궁금할 수 있다. 
> 마찬가지로 Resource Owner의 일을 수행 해주는 client가 정말 그 client일까 하는 물음이 있다.
> 이런 의미에서 Resource Server는 Resource Owner의 브라우저를 통해 client를 구분하는 값을 전달한다.

#
### Resource Owner 승인과정
1. 사용자(Resource Owner)는 서비스(Client)를 이용하기 위해 로그인 페이지에 접근한다.
2. 그럼 서비스(Client)는 사용자(Resource Owner)에게 로그인 페이지를 제공하게 된다. 로그인 페이지에서 사용자는 "페이스북/구글 으로 로그인"버튼을 누른다.

<img width="855" alt="스크린샷 2023-06-11 오후 2 03 21" src="https://github.com/HyunSu1768/TIL/assets/108796235/e1f5b208-8d04-4648-a83d-b1f66137b213">

3. 만일 사용자가 Login with Facebook 버튼을 클릭하게 되면, 특정한 url이 페이스북 서버쪽으로 보내지게 된다.
<img width="824" alt="스크린샷 2023-06-11 오후 2 04 52" src="https://github.com/HyunSu1768/TIL/assets/108796235/90234e61-c361-49bc-addc-e2f650b2413d">
<img width="859" alt="스크린샷 2023-06-11 오후 2 05 45" src="https://github.com/HyunSu1768/TIL/assets/108796235/456e6273-1df1-4083-8653-6fb73a2d5189">

4. 클라이언트로부터 보낸 서비스 정보와, 리소스 로그인 서버에 등록된 서비스 정보를 비교한다.
<img width="812" alt="스크린샷 2023-06-11 오후 2 08 39" src="https://github.com/HyunSu1768/TIL/assets/108796235/1417f8d8-d569-4512-af54-e42001d42cde">

4-1. 확인이 완료되면, Resource Server로 부터 전용 로그인 페이지로 이동하여 사용자에게 보여준다.
<img width="832" alt="스크린샷 2023-06-11 오후 2 10 14" src="https://github.com/HyunSu1768/TIL/assets/108796235/f94244d1-beb7-4ecf-b1fe-a2289036b134">
<img width="854" alt="스크린샷 2023-06-11 오후 2 10 28" src="https://github.com/HyunSu1768/TIL/assets/108796235/ca4b0d38-990a-4792-aaee-da0c5b9cf55f">

5. ID/PW를 적어서 로그인을 하게되면, client가 사용하려는 기능(scope)에 대해 Resource Owner의 동의(승인)을 요청한다.
<img width="822" alt="스크린샷 2023-06-11 오후 2 12 13" src="https://github.com/HyunSu1768/TIL/assets/108796235/6e3ba7d3-5f86-49b5-bcbb-f9dcc9b055e1">
<img width="780" alt="스크린샷 2023-06-11 오후 2 12 24" src="https://github.com/HyunSu1768/TIL/assets/108796235/a49f31c2-3dca-44f3-a05b-787f4627fd30">
<img width="854" alt="스크린샷 2023-06-11 오후 2 12 46" src="https://github.com/HyunSu1768/TIL/assets/108796235/f13105e6-8618-48e4-98a2-17df30f63a99">

5-1. Resource Owner가 Allow 버튼을 누르면 Resource Owner가 권한을 위임햇다는 승인이 Resource Server에 전달된다.
<img width="525" alt="스크린샷 2023-06-11 오후 2 13 30" src="https://github.com/HyunSu1768/TIL/assets/108796235/a07f95bb-a044-475d-9c66-4748d5fb314d">
이로써 Resource Server가 갖는 정보는 다음과 같다.
1. Client Id : Resource Owner와 연결된 client가 누군지
2. Client Secret : Resource Owner와 연결된 client의 비밀번호
3. Redirect URL : Client와 통신할 통로
4. user id : client와 연결된 Resource Owner의 id
5. scope : client가 Resource Owner대신에 사용할 기능들

6. 하지만, 이미 Owner가 Client에게 권한 승인을 했더라도 아직 Server가 허락하지 않았다. 따라서 Resource Server도 Client에게 권한 승인을 하기 위해 Authorization code를 Redirect URL을 통해 사용자에게 응답하고
7. 다시 사용자는 그대로 Client에게 다시 보낸다.
<img width="770" alt="스크린샷 2023-06-11 오후 2 16 28" src="https://github.com/HyunSu1768/TIL/assets/108796235/41810f5c-9c26-4b42-a61b-7fbef1d5da3d">
<img width="857" alt="스크린샷 2023-06-11 오후 2 16 52" src="https://github.com/HyunSu1768/TIL/assets/108796235/76cdff67-c4c4-48c2-9ed7-0e7bad2a24ef">

이를 통해, client는 Resource Server가 보낸 Authorization code, "code=3"를 Resource Onwer를 통해 받는다.
<img width="812" alt="스크린샷 2023-06-11 오후 2 19 05" src="https://github.com/HyunSu1768/TIL/assets/108796235/8b3036a7-b3ea-48f0-a4be-f26ca0a6b277">
8. 이제 Client가 Resource Server에게 직접 url을 보낸다.

<img width="824" alt="스크린샷 2023-06-11 오후 2 19 36" src="https://github.com/HyunSu1768/TIL/assets/108796235/a54dbf2c-a16a-41a9-8e90-b467b5e36d8c">
<img width="857" alt="스크린샷 2023-06-11 오후 2 19 44" src="https://github.com/HyunSu1768/TIL/assets/108796235/71f2055e-7cb8-426a-9fed-74bcff95b47a">

9. 그럼 Resource Server는 Client가 전달한 정보들을 비굑해서 일치한다면, Access Token을 발급한다. 그리고 이제 필요없어진 Authorization code는 지운다.
10. 그렇게 토큰을 받은 Client는 사용자에게 최종적으로 로그인이 완료되었다고 응답한다.

<img width="873" alt="스크린샷 2023-06-11 오후 2 21 34" src="https://github.com/HyunSu1768/TIL/assets/108796235/934b8257-6a8c-4618-b5a7-062b194954ca">
<img width="856" alt="스크린샷 2023-06-11 오후 2 21 41" src="https://github.com/HyunSu1768/TIL/assets/108796235/df467ea1-8cf9-4b05-949c-4f6439bb76f7">

11~14. 이제 client는 Resource Server의 api를 요청해 Resource Owner의 Id혹은 프로필 정보를 사용할 수 있다.
<img width="918" alt="스크린샷 2023-06-11 오후 2 22 50" src="https://github.com/HyunSu1768/TIL/assets/108796235/739fa8ed-2564-4d7b-999c-4978823dbbca">
<img width="853" alt="스크린샷 2023-06-11 오후 2 23 04" src="https://github.com/HyunSu1768/TIL/assets/108796235/8e7fa16c-1f8b-49d2-bd28-048d9ccb797d">

15. Access Token이 기간이 만료되어 401에러가 나면, Refresh Token을 통해 Access Token을 재발급 한다.
<img width="779" alt="스크린샷 2023-06-11 오후 2 24 01" src="https://github.com/HyunSu1768/TIL/assets/108796235/3675123b-d0ff-4f9e-96d6-8f40f18f2ab1">

[Spring Boot OAuth2.0 실습 리포지토리](https://github.com/HyunSu1768/Oauth2-login)
