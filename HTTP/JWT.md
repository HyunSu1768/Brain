출처 : https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#jwt_json_web_token_%EC%9D%B4%EB%9E%80

### JWT (json web token) 이란
* JWT(JSON WEB TOKEN)란 인증에 필요한 정보들을 암호화시킨 JSON 토큰이다.
* JWT기반 인증은 JWT토큰을 HTTP헤더에 실어 서버가 클라이언트를 식별하는 방식이다.
* JWT는 JSON 데이터를 Base64 URLL-safe Encode를 통해 인코딩ㅎ여 직렬화한 것이며, 토큰 내부에는 위변조 방식을 위해 전자서명도 포함돼 있다.
* JWT를 서버로 전송하면 서버는 서명을 검증하는 과정을 거치게 되며 검정이 완료되면 요청한 응답을 돌려준다.
###### Base64 URL-safe Encode 는 일반적은 Base64 Encode 에서 URL 에서 오류없이 사용하도록 '+', '/' 를 각각 '-','_'로 표현한 것이다.

### JWT 구조
* JWT는 . 을 구분자로 나누어지는 세 가지 문자열의 조합이다.
* . 을 기준으로 좌측부터 Header.Payload.Signature 을 의미한다.
* Header에는 JWT에서 사용할 타입과 해시 알고리즘을 포함한고 Payload는 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다.
* Signature에는 Header,Payload를 Base64 URL-safe Encode 를 한 이후 Header에 명시된 해시함수를 적용하고, 개인키로 서명한 전자서명이 담겨있다.

#### 구조
##### Header
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```
* alg : 서명한 암호화 알고리즘
* typ : 토큰 유형

##### Payload
* 토큰에서 사용할 정보의 조각들인 Claim이 담겨있다. (실제 JWT 를 통해서 알 수 있는 데이터)
  * key-value 형식으로 이루어진 한 쌍의 정보를 Claim이라고 칭한다.
* 서버와 클아이언트가 주고받는 시스템에서 실제로 사용될 정보에 대한 내용을 담고 있는 섹션
```
{
  "sub" : "1234567890",
  "name" : "John Doe"
  "iat" : 1516239022
}
```
* 페이로드는 정해진 타입은 없지만, 대표적으로 Registered claims, Public claims, Private claims 이렇게 세 가지로 나뉜다.
```
{
  "jti": "1000",
  "exp": "1521430000000",
  "https://kevin.tistory.com": true,
  "username": "kevin"
}
```
* Registed claims: 미리 정의된 클레임.
  * iss(issuer; 발행자),
  * exp(expireation time; 만료 시간),
  * sub(subject; 제목),
  * iat(issued At; 발행 시간),
  * jti(JWI ID)

* Public claims: 사용자가 정의할 수 있는 클레임 공개용 정보 전달을 위해 사용.
* Private claims: 해당하는 당사자들 간에 정보를 공유하기 위해 만들어진 사용자 지정 클레임. 외부에 공개되도 상관없지만 해당 유저를 특정할 수 있는 정보들을 담는다.

* Signature
```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  your-256-bit-secret
)
```
* 시그니처에서 사용하는 알고리즘은 헤더에서 정의한 알고리즘 방힉(alg)을 활용한다.
* 시그니처의 구조는 (헤더 + 페이로드)와 서버가 갖고 있는 유일한 key값을 합친 것을 헤더에서 정의한 알고리즘으로 암호화를 한다.
