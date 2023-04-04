### @AutoWired 필드 명, @Qaulifier @Primary
* 조회 대상 빈이 2개 이상일때 
  * @AutoWired 필드 명 매칭
  * @Qaulifier -> @Qaulifier 끼리 매칭 -> 빈 이름 매칭
  * @Primary 사용
#### @Autowired 필드 명
* @Autowired는 타입 매칭을 시도하고 이때 여러 빈이 있으면 필드이름 , 파라미터 이름으로 빈 이름을 추가 매칭한다.
#### @Qaulifier 사용
* @Qaulifier 는 추가 구분자를 붙여주는 방법이다. 주입시 추가적인 방법을 제공하는 것이지 빈 이름을 바꾸는것은 아니다.
#### @Primary
* 우선순위 정하는 방법이다. 여러개의 빈이 조회될때 Primary 가 우선권을 가진다.
#### @Primary 와 @Qualifier 가 겹칠때
* 더 세세하게 설정된 @Qualifier 가 우선권을 가진다.
