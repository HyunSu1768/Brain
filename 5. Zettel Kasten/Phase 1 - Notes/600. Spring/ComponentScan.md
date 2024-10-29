### 컴포넌트 스캔
```
@Configuration
@ComponentScan(
        excludeFilters = @ComponentScan.Filter(type = FilterType.ANNOTATION, classes = Configuration.class)
)
public class AutoAppConfig {

}
```
* @ComponentScan 어노테이션을 쓰게되면 @Components가 있는 클래스를 모두 스프링 빈에 자동으로 등록된다. 이제 @Bean 을 쓰고 일일히 등록해야 하지 않아도 된다.
* 하지만 여기서 의존성을 주입받는 생성자가 작동하지 않을것이다. 그래서 @AutoWired 어노테이션을 써주면 스프링 컨테이너에서 생성자가 원하는 타입을 찾아 자동으로 주입해 준다.
```
    @Autowired
    public OrderServiceImpl(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
    }
```
```
    @Autowired
    public MemberServiceImpl(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }
```

### 테스트케이스 작성하기
```
public class AutoAppConfigTest {

    @Test
    void basicScan(){
        AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AutoAppConfig.class);

        MemberService bean = ac.getBean(MemberService.class);
        Assertions.assertThat(bean).isInstanceOf(MemberService.class);

    }
}
```
* 전에 했던 테스트와 똑같다. 스프링 컨테이너를 AppCofig에서 AutoAppConfig로 바꿔주면 된다.
