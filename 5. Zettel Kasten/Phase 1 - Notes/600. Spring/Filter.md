![img](https://user-images.githubusercontent.com/45676906/116671110-86d57480-a9db-11eb-98e8-00e944812410.png)
### Spring Filter란?
* Filter는 말 그대로 어떠한 것을 걸러내는 역할을 합니다.
* DispatcherServler 앞에 Filter가 존재하는것을 보면, 클라이언트의 요청에 대해서 사전에 걸러내는 역할을 합니다.
* 또한 Response를 줄 때도 변경 처리를 할 수 있다는 특징을 가지고 있습니다.
* 즉 Request, Response에 대해서 처리하는 과정이라고 생각하면 이해하기 쉽습니다.

대표적으로 Filter 라는 인터페이스가 존재합니다. 인터페이스 내부에는 init(), doFilter(), destroy() 메소드가 존재합니다.
* init() : 필터 인스턴스 초기화
* doFilter() : 전/후 처리
* destroy() : 필터 인스턴스 종료
간단하게 이렇게 말할 수 있으며 메소드의 이름과 크게 다르지 않습니다.
```
@Component
public class FilterTest implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("Filter init");
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        System.out.println("do Filter");
        chain.doFilter(request, response);
    }

    @Override
    public void destroy() {
        System.out.println("Filter Destroy");
    }
}
```
* 그릐고 하나의 API에 접근해보면 위와 같이 init, deFilter, destroy 메소드 로그가 찍히는 것을 볼 수 있습니다. init은 한번의 초기화가 이루어지고, destroy도 WAS가 종료 될 때 실행됩니다.
* doFilter는 요청이 들어올 때마다 실행이 되는 것도 확인할 수 있습니다. 즉 Filter를 위한 로직은 doFilter에 작성하면 됩니다.

### 그리고...
* 맨 위의 그림을 보면 Filter Chain이 존재하는데 그림에서도 알 수 있듯이 Filter는 하나만 고성할 수 있는 것이 아니고 여러 개로 구성할 수 있습니다.
* 이럴때는 chain.doFilter(request, response)를 이용하여 다음 필터로 연결시킬 수 있습니다.
