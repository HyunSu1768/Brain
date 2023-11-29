---
aliases: 
tags:
---


---


Source : 테라폼으로 시작하는 IaC
Author : 
URL :

## for_each
- 모듈 또는 리소스 블록에서 for_each에 입력된 값이 map 또는 set이면 Key의 값 개수만큼 리소스를 생성하게 된다. 
```
resource "local_file" "abc" {
	for_each = {
		a = "content a"
		b = "content b"
	}
	content = each.value
	filename = "${paht.module}/${each.value}.txt"
}
```
이와같이 each.value를 통해 for_each의 key에 대응하는 value를 사용할 수 있다.
또한 each.key를 사용해서 key를 사용할 수 있다.

### Link of Thoughts
Area : #300-DevOps/340-Provisioning 

Keywords :
- 

Related Notes : 
- [[Count란]]