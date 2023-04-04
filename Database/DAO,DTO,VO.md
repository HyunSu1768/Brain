### DAO(Data Access Object)
* DAO는 Data Access Object의 약자로, DB의 데이터에 접근하기 위한 객체를 가리킨다.DB에 접근하기 위한 로직을 분리하기 위해 사용한다. 직접 DB에 접근하여 data를 삽입, 삭제, 조회 등 조작할 수 있는 기능을 수행한다.

### DTO(Data Transfer Object)
* DTO는 Data Transfer Object의 약자로, 계층 간(Controller, View, Business Layer)데이터 교환을 위한 Java Bean를 의미한다. DTO는 로직을 가지지 않는 데이터 객체이고, getter, setter 메소드만 가진 클래스를 의미한다.

### VO(Value Object)
* VO는 Value Object의 약자로, Read-Only 속성을 가진 값 오브젝트 이다. 자바에서 단순히 값 타입을 표현하기 위하여 불변 클래스를 만들어 사용한다. 따라서 getter 기능만 존재한다.

### DTO vs VO
* DTO는 가변의 성격을 가진 클래스이며 데이터 전송을 위해 존재한다. 따라서 getter와 setter기능을 모두 가지고 있다.
* 그에 반해, VO는 값 그 자체의 의미를 가진 불변 클래스를 의미한다. 따라서 getter기능만 존재한다.
