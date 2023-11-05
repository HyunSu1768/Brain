<aside>
💡 Filter 의 역할

---

- Spring 에서의 Filter는 HTTP요청 처리과정에서 요청과 응답 사이의 데이터를 변경하거나 가로채는 등의 역할을 수행하는 객체이다. 요청과 응답 사이에 존재하여, 요청을 처리하는 서블릿에 도달하기 전에 요청을 가로채어 필터가 처리를 수행하고, 그 후 처리 결과를 다시 응답으로 반환한다.
- 예를 들어, 인증 정보 검증, 권한 부여, 로깅, 인코딩, CORS 처리 등의 작업을 필터에서 수행할 수 있다. 이러한 작업들을 통해 보안, 성능, 품질 등을 향상시킬 수 있다.
</aside>

<aside>
💡 Spring Filter란?

---

- Spring Framework에서 제공하는 기능으로, Servlet API 를 사용하여 HTTP요청에 대한 처리를 하는 웹 애플리케이션이다.

<aside>
💡 Servlet API란?

---

- Java 웹 애플리케이션을 개발할  때 사용되는 API로 Servlet Container에서 제공된다.
    - Servlet Container는 Servlet API를 구현하여 HTTP요청에 대한 처리를 수행하는 웹 애플리케이션 서버이다.
</aside>

- 이 Servlet API를 사용하여 HTTP에 대한 요청을 수행하며, 요청이 컨트롤러에 도달하기 전에 요청과 응답을 변경하거나 추가적인 작업을 할 수 있다.
- Spring Filter는 다양한 기능을 수행할 수 있다. 예를들어, 요청의 인코딩 설정, 보안 처리, 캐싱 처리 등의 작업을 수행할 수 있다. 그리고 Spring Security와 같은 보안 프레임워크를 사용하여 애플리케이션의 보안 기능을 강화할 수 있다.
</aside>

<aside>
💡 Spring Security Filter란?

---

- Spring Security 프레임워크에서 제공하는 기능으로, HTTP 요청에 대한 보안 처리를 수행하는 필터이다.
    - javax.servlet.Filter 인터페이스를 구현하여 작성된다. 이 인터페이스는 HTTP요청에 대한 필터링 작업을 수행하는 메소드인 doFilter()를 정의하고 있다.

<aside>
💡 용어정리

</aside>

- Authentication(인증) : 인증 정보를 나타낸다. 인증 정보는 사용자의 ID와 비밀번호 등의 정보로 구성된다.
- Authorization(인가) : 권한 부여를 나타낸다. 권한은 인증된 사용자가 특정 리소스에 대해 수행할 수 있는 작업을 나타낸다.
- UserDetailService : 사용자 정보를 가져오는 인터페이스이다. Spring Security에서는 이 인터페이스를 구현하여 사용자의 정보를 가져올 수 있다.
- AuthenticationManager : 인증을 수행하는 객체이다. 사용자가 제공한 인증 정보를 검증하고, 인증이 성공하면 인증된 사용자 객체를 생성한다.
- SecurityContextHolder : 현재 인증된 사용자 정보를 저장하는 객체이다. 인증된 사용자 정보는 다른 객체에서도 사용될 수 있다.
- FilterChainProxy : 여러 개의 Spring Security Filter를 체인 형태로 연결하여 동작하도록 하는 필터 이다. FilterChainProxy는 실제 필터링 작업을 수행하는 FilterChain 을 관리한다.
</aside>
