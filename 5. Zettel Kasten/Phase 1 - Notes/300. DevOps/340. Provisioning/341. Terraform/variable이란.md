---
aliases:
  - Terraform
tags:
  - 문헌메모
  - 완료
---


---


Source : 테라폼으로 시작하는 IaC
Author : 
URL :

- 입력 변수는 인프라를 구성하는 데 필요한 속성 값을정의해 코드의 변경 없이 여러 인프라를 생성할 수 있도록 해줌

```
variable "<이름>" {
	<인수> = <값>
}
variable "image_id" {
	type = string
}
```

### 변수 이름으로 사용 불가능한 이름
- source
- version
- providers
- count
- for_each
- lifecycle
- depends_on
- locals

### 메타인수
- default : 변수에 할당되는 기본값
- type : 변수에 허용되는 값 유형 정의
- description : 입력 변수 설명
- validation : 변수 선언의 제약조건을 추가해 유효성 검사 규칙을 정의
- sensitive : 민감한 변수 값임을 알리고 테라폼의 출력문에서 값 노출을 제한
- nullable : 변수에 값이 없어도 됨을 지정

### 변수 유형
- 기본 유형
	- string : 글자 유형
	- number : 숫자 유형
	- bool : true 또는 false
	- any : 명시적으로 모든 유형이 허용됨을 알림
- 집합 유형
	- list(<유형>) : 인덱스 기반 집합
	- map(<유형>) : 값 = 속성 기반 집합이며 키값 기준 정렬
	- set(<유형>) : 값 기반 집합이며 정렬 키값 기준 정렬
	- object({<인수 이름>=<유형>, ..}) 
	- tuple

### 유효성 검사
- 0.13.0 버전부터 사용자 지정 유효성 검사가 가능하다
```
variable "image_id" {
	type = string
	description = "The id of the machine image (AMI) to use for the server"

	validation {
		condition = length(var.image_id) > 4
		error_message = "The image_id value must exceed 4"
	}

	validation {
		# regex(...) fails if it cannot find a match
		condition = can(regex("^ami-", var.image_id))
		error_message = "The image_id value must starting with \"ami-\"."
	}
}
```


### 변수 참조
- variable은 코드 내에서 var.<이름> 으로 참조된다.
```
variable "my_password" {}

resource "local_file" "abc" {
	content = var.my_password
	filename = "${path.module}/abc.txt"
}
```

### 민감한 변수 취급
- 테라폼 0.14.0버전부터 입력 변수의 민감 여부를 선언할 수 있음
```
variable "my_password" {
	default = "password"
	sensitive = true
}

resource "local_file" "abc" {
	content = var.my_password
	filename = "${path.module}/abc.txt"
}
```
이렇게 된다면, terraform apply를 했을 때 (sensitive) 라고 감춰지게 된다.

### 변수 입력 방식과 우선순위 수준
- variable 의 목적은 코드 내용을 수정하지 않고 테라폼의 모듈적 특성을 통해 입력되는 변수로 재사용성을 높이는 데 있다.
1. 실행 후 입력 : 변수에 값이 선언되지 않아 CLI에서 입력한다.
2. variable 블록의 default 값
3. 환경 변수(TF_VAR_변수이름) 
4. terraform.tfvars에 정의된 변수 선언
5. * .auto.tfvars에 정의된 변수 선언
6. * .auto.tfvars.json 에 정의된 변수 선언
7. CLI실행 시 -var 인수에 지정 또는 -var-file로 파일 지정

### Link of Thoughts
Area : #300-DevOps/340-Provisioning 

Keywords :
- 

Related Notes : 
- 