Spring Security는 사용자 인증과 인가를 처리하는데 필요한 많은 기능들을 제공합니다.
UserDetailsService 인터페이스와 UserDetails 인터페이스는 사용자 인증에 중요한 역할을 합니다.

### UserDetails 인터페이스
* 이 인터페이스는 Spring Seurity에서 사용자의 정보를 담는 인터페이스입니다.
* 보통은 사용자의 아이디, 패스워드, 권한 정보 등을 가지고 있습니다.
* 이 인터페이스를 구현한 클래스를 CustomUserDetails라고 부르고, 애플리케이션의 사용자 정보를 담는데 사용합니다.

### 'UserDetails' 인터페이스에는 다음과 같은 메소드들이 있다.
* 'Collection<? extends GrantedAuthority> getAuthorities()' : 사용자에게 부여된 권한을 반환합니다.
* 'String getPassword()' : 사용자의 패스워드를 반환합니다.
* 'String getUsername()' : 사용자의 이름을 반환합니다.
* 'boolean isAccountNotExpired()' : 사용자 계정이 만료되지 않았는지를 반환합니다.
* 'boolean isAccountNonLocked()' : 사용자 계정이 잠기지 않았는지를 반환합니다.
* 'boolean isCredentialsNonExpired()' : 사용자의 자격 증명이 만료되지 않았는지를 반환합니다.
* 'boolean isEnabled()' : 사용자 계정이 활성화되었는지를 반환합니다.

### 'UserDetailsService'
* 'UserDetailsService'는 사용자의 정보를 로드하는 역할을 하는 인터페이스 입니다.
* 이 인터페이스를 구현한 클래스를 'CustomUserDetailsUser'라고 부르며, 이를 통해 애플리케이션의 사용자 정보를 Spring Security로 로드할 수 있습니다

'UserDetailsService' 인터페이스에는 다음과 같은 메소드가 정의되어 있습니다.

* 'UserDetails loadUserByuUsername(String username) throws UsernameNotFoundException' : 주어진 username에 해당하는 사용자의 'UserDetails' 를 로드합니다.

'CustomUserDetails'와 'CustomUserDetailsService'를 이용하면, Spring Security에서 제공하는 기본 사용자 정보 모델이나 서비스를 사용하는 대신, 애플리케이션에 특화된 사용자 정보 모델이나 로직을 사용할 수 있게 된다.
이를 통해 애플리켕이션의 요구사항에 더욱 잘 맞는 보안 기능을 구현할 수 있다.
