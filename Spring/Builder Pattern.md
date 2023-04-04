### Builder Pattern 이란?
* 복합 객체의 생성 과정과 표현 방법을 분리하여 동일한 생성 절차에서 서로 다른 표현 결과를 만들 수 있게 하는 패턴
* 예를들어 생성자 인자로 너무 많은 인자를 받을때 어떠한 인자가 어떠한 값을 나타내는지 확인하기 힘듦
* 그리고 어떠한 값에는 NULL을 넣어야 하는데 이는 코드 가독성 측면에서 좋지 않다

#### 빌더패턴 예시
```
Hero mage = new Hero
	.Builder(Profession.MAGE, "Riobard")
	.withHairColor(HairColor.BLACK)
	.withWeapon(Weapon.DAGGER)
	.build();
```
