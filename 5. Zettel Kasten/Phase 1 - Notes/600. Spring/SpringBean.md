### 스프링 컨테이너 생성
```
ApplicatioinContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
```
##### AppConfig.class
```
@Configuration
public class AppConfig {
    @Bean
    public MemberService memberService(){
        System.out.println("AppConfig.memberService");
        return new MemberServiceImpl(MemberRepository());
    }
    @Bean
    public MemberRepository MemberRepository() {

        System.out.println("AppConfig.MemberRepository");
        return new MemoryMemberRepository();
    }
    @Bean
    public OrderService orderService(){

        System.out.println("AppConfig.orderService");
        return new OrderServiceImpl(MemberRepository(),discountPolicy() ) ;
    }
    @Bean
    public DiscountPolicy discountPolicy(){
        return new RateDiscountPolicy();
    }
}
``` 
* ApplicationContext 를 스프링 컨테이너라고 한다.
* ApplicationContext 는 인터페이스이다.
* 스프링 컨테이너는 XML, 애노테이션 기반 자바 설정 클래스로도 만들수 있다.
* AppConfig가 애노테이션 기반 자바 설정 클래스로 스프링 컨테이너를 만든거다.
### 스프링 빈 등록
* 빈 이름은 메서드 이름을 사용한다.
* 빈 이름을 직접 부여할 수도 있다. [ @Bean(name = " ")

### 컨테이너에 등록된 모두 빈 조회
```
public class ApplicationContextInfoTest {
    AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);

    @Test
    @DisplayName("모든 빈 출력하기")
    public void findAllBean(){
        String[] beanDefinitionNames = ac.getBeanDefinitionNames();
        for (String beanDefinitionName : beanDefinitionNames) {
            Object bean = ac.getBean(beanDefinitionName);


        }
    }
    @Test
    @DisplayName("애플리케이션 빈 출력하기 ")
    public void findApplicationBean(){
        String[] beanDefinitionNames = ac.getBeanDefinitionNames();
        for (String beanDefinitionName : beanDefinitionNames) {
            BeanDefinition beanDefinition = ac.getBeanDefinition(beanDefinitionName);

            if (beanDefinition.getRole() == BeanDefinition.ROLE_APPLICATION) {
                Object bean = ac.getBean(beanDefinitionName);
                System.out.println("name = " + beanDefinitionName + "object = " + bean);
            }
        }
    }

}
```
* 모든 빈 출력하기
  * 실행하면 스프링에 등록된 모든 빈 정보를 출력할 수 있다.
  * ac.getBeanDefinitionNames(); 를 사용하면 모든 빈 이름을 조회할 수 있다.
  * ac.getBean(); 빈 이름으로 빈 객체를 조회한다.
* 애플리케이션 빈 출력하기
  * 스프링 자체에서 등록한 빈은 제외하고, 내가 등록한 빈만 출력할 수 있다.
  * 스프링이 내부에서 사용하는 빈은 getRole()로 구분할 수 있다.
    * ROLE_APPLICATIOIN: 일반적으로 사용자가 정의한 빈
    * ROLE_INFRASTRUCTURE : 스프링이 내부에서 사용하는 빈

### 스프링 빈 조회 - 기본
<br>
#### 스프링 컨테이너에서 스프링 빈을 찾는 가장 기본적인 방법
* ac.getBean(빈이름, 타입)
* ac.getBean(타입)
  * 조회 대상 스프링 빈이 없으면 예외가 발생한다. [ NoSuchBeanDefinitionException ]
``` 
public class ApplicationContextBasicFindTest {
    AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);

    @Test
    @DisplayName("타입 으로 조회")
    void findBeanByType() {
        MemberService memberService = ac.getBean(MemberService.class);
        assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
    }

    @Test
    @DisplayName("구체 타입으로 조회")
    void findBeanByName() {
        MemberService memberService = ac.getBean("memberService", MemberServiceImpl.class);
        assertThat(memberService).isInstanceOf(MemberServiceImpl.class);
    }

    @Test
    @DisplayName("빈 이름으로 조회X")
    void findBeanByNameX(){
//        MemberService xxxxx = ac.getBean("xxxxx", MemberService.class);
        assertThrows(NoSuchBeanDefinitionException.class, () -> ac.getBean("xxxxx", MemberService.class));
    }
}
```

### 스프링 빈 조회 - 동일한 타입이 두개 이상일때
* 타입으로 조회시 같은 타입의 스프링 빈이 둘 이상이면 오류가 발생한다. 이때는 이름을 지정한 후 사용한다.
* ac.getBeansOfType() 을 사용하면 모든 종류의 빈을 조회할 수 있다.
```
public class ApplicationContextExtendsFindTest {
    AnnotationConfigApplicationContext ac = new AnnotationConfigApplicationContext(TestConfig.class);

    @Test
    @DisplayName("부모 타입으로 조회시, 자식이 둘 이상 있으면, 중복 오류가 발생한다")
    void findBeanByParentTypeDuplicate(){
        assertThrows(NoUniqueBeanDefinitionException.class,()->ac.getBean(DiscountPolicy.class));
    }
    @Test
    @DisplayName("부모 타입으로 조회시, 자식이 둘 이상 있으면, 중복 오류가 발생한다")
    void findBeanByParentTypeBeanName(){
        DiscountPolicy rateDiscountPolicy = ac.getBean("rateDiscountPolicy", DiscountPolicy.class);
        assertThat(rateDiscountPolicy).isInstanceOf(RateDiscountPolicy.class);
    }

    @Test
    @DisplayName("특정 하위 타입으로 조회")
        void findBeanBySubType(){
        RateDiscountPolicy bean = ac.getBean(RateDiscountPolicy.class);
        assertThat(bean).isInstanceOf(RateDiscountPolicy.class);
    }

    @Test
    @DisplayName("부모 타입으로 모두 조회하기")
    void findAllBeanByParentType(){
        Map<String, DiscountPolicy> beansOfType = ac.getBeansOfType(DiscountPolicy.class);
        assertThat(beansOfType.size()).isEqualTo(2);
        for (String key : beansOfType.keySet()) {
            System.out.println("key = " + key + " value = " + beansOfType.get(key));
        }
    }

    @Test
    @DisplayName("부모 타입으로 모두 조회하가ㅣ - Obejct")
    void findAllBeanByObject(){
        Map<String, Object> beansOfType = ac.getBeansOfType(Object.class);
        for (String key : beansOfType.keySet()) {
            System.out.println("key = " + key + " value = " + beansOfType.get(key));

        }
    }


    @Configuration
    static class TestConfig {
        @Bean
        public DiscountPolicy rateDiscountPolicy() {
            return new RateDiscountPolicy();
        }

        @Bean
        public DiscountPolicy fixDiscountPolicy() {
            return new FixDiscountPolicy();
        }
    }
}
```

### 스프링 빈의 상속관계
* 부모 타입으로 조회하면, 자식 타입도 조회된다.
* Object 타임으로 조회하면 모든 스프링 빈을 조회한다.
