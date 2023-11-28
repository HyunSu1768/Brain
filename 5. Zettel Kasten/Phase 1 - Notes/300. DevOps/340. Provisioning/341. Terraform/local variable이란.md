---
aliases:
  - Terraform
tags:
  - 완료
  - 문헌메모
---


---


Source : 테라폼으로 시작하는 IaC
Author : 
URL :

# local(지역 값)
- 코드 내에서 사용자가 지정한 값 또는 속성 값을 가공해 참조 가능한 지역 값이다.
- 코드 내에서만 가공되어 동작하는 값을 선언한다.
- 외부에서 입력되지 않는다.
- [[variable이란]] (입력 변수) 와 달리 선언된 모듈 내에서만 접근 가능하다
- 반복적으로 사용할 수 있는 편의 제공


## local 선언
- locals로 시작한다
- locals에 선언한 로컬 변수 이름은 전체 루트 모듈 내에서 유일해야 한다.
```
variable "prefix" {  
  default = "hello"  
}  
  
locals {  
  name = "terraform"  
  content = "${var.prefix} ${local.name}"  
  my_info = {  
    age = 20  
    region = "KR"  
  }  
  my_nums = [1,2,3,4,5]  
}  
  
locals {  
  content = "content2" # 중복된 값이 선언되어 오류가 발생한다.  
}
```

## local 참조
- local.<이름> 으로 참조할 수 있다.
- 테라폼 구성 파일을 여러 개 생성해 작업하는 경우 서로 다른 파일에 선언되어 있더라도 참조할 수 있다.

### Link of Thoughts
Area : #300-DevOps/340-Provisioning 

Keywords :
- 

Related Notes : 
- 

