---
aliases:
  - Terraform
tags:
  - 완료
  - 300-DevOps/340-Provisioning
---


---


Source : 테라폼으로 시작하는 IaC
Author : 
URL :

# Output
- 테라폼 코드의 프로비저닝 수행 후의 결과 속성 값을 확인하는 용도로 사용됨
- 코드 내 요소 간에 노출을 제한하듯 테라폼 모듈 간, 워크스페이스 간 데이터 접근 요소로도 활용할 수 있음

## Output 선언
```
output "instance_ip_addr" {
	value = "http://${aws_instance.server.private_ip}"
}
```

## 메타 인수
- description : 출력 값 설명
- sensitive : 민감한 출력 값임을 알리고 테라폼의 출력문에서 값 노출을 제한
- depends_on : value에 담길 값이 특정 구성에 종속성이 있는 경우 생성되는 순서를 임의로 조정
- precondition : 출력 전에 지정된 조건을 검증

### Link of Thoughts
Area : #300-DevOps/340-Provisioning 

Keywords :
- 

Related Notes : 
- 