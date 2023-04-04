<aside>
💡 Spring Security + JWT 흐름 이해

---

<aside>
💡 스프링 시큐리티

---

- 어플리케이션 보안을 담당하는 프레임워크

<aside>
💡 특징

---

- Filter를 기반으로 동작한다.
- Bean으로 설정할 수 있다.
</aside>

<aside>
💡 용어

---

- 접근 주체(Principal): 보호된 대상에 접근하는 유저
- 인증 : 현재 유저가 누구인지 확인(로그인)
    - 어플레이케이션의 작업을 수행할 수 있는 주체임을 증명한다.
- 인가(Authorize) : 현재 유저의 권한을 검사한다.
    - 어떤 페이지, 리소스 등에 접근할 수 있는지를 검사한다.
    - 권한 부여 영역
        - 웹 요청 권한
        - 메소드 호출 및 도메인 인스턴스에 대한 접근 권한
</aside>

</aside>

<aside>
💡 Spring Security 구조

---

- Http Request 수신
    - Spring Security는 필터로 동작을 한다.
    - 요청이 들어오면, 인증과 권한을 위한 필터들을 통하게 된다.
    - 유저가 인증을 요청할때 인증 매커니즘과 모델을 기반으로한 필터들을 통과한다.
    - 예
        - HTTP기본 인증을 요청하면 BasicAuthenticationFilter를 통과한다.
        - HTTP Digest 인증을 요청하면 DigestAuthenticationFilter를 통과한다.
        - 로그인 폼에 의해 요청된 인증은 UserpasswordAuthenticationFilter를 통과한다.
        - x509 인증을 요청하면 X509AuthenticationFilter를 통과한다.
- 유저 자격을 기반으로 인증토큰(AuthenticatioinToken) 만들기
    - username과 password를 요청으로 추출하여 유저 자격을 기반으로 인증 객체를 생성한다.
        - 대부분의 인증매커니즘은 username과 password를 기반으로 한다.
        - username과 password는 UsernamePasswordAuthenticationToken을 만드는데 사용된다.
- Filter를 통해 AuthenticationToken을 AuthenticationManager에 위임한다.
    - UsernamePasswordAuthenticationToken오브젝트가 생성된 후, AuthenticationManager의 인증 메소드를 호출 한다.
    - AuthenticationManager는 인터페이스로 정의되어있다.
        - 실제 구현은 ProviderManager에서 한다.

```java
public interface AuthenticationManager{
  Authentication authenticate(Authentication authentication) throws AuthenticationException;
}
```

- 실제 프로래그래밍 구현에서 AuthenticationManager를 사용하기 위해 설정에 AuthenticationManagerBuilder를 이용해 아래에 정의된 UserServiceDetails를 매핑시켜준다.
    - 여기서는 LoginService가 UserDetailsService를 구현하였으므로, LoginService가 UserDetailService의 역할을 한다.
</aside>

</aside>
