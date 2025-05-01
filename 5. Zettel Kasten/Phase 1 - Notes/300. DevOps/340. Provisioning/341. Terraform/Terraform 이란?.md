---
aliases:
  - Terraform
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

# 역사로 이해하기 - Terraform은 왜 나왔을까?

## 1. 과거 : 수동 서버 관리 → 구성 관리 도구의 등장

과거의 인프라 운영 방법

- 서버를 사람이 직접 구매, 설치 ( On-Premise )
- 웹 서버, DB, 로드밸런서 설정도 수작업으로 진행
- 시간이 매우 오래걸리며 사람이 하는것이기 때문에 실수를 할 수 있음

이를 해결하기 위해 등장한 도구들:

- Puppet, Chef : 서버 설정을 코드로 관리하는 “구성 관리” 도구
- Ansible : SSH 기반의 더 쉬운 설정 관리 도구

하지만 위 도구 모두 서버가 이미 존재해야 작동이 가능했다.

## 2. 클라우드의 등장 → 인프라를 코드로 다루려는 수요 증가

- AWS 와 같은 클라우드 컴퓨팅 서비스가 생기면서, 버튼 클릭 몇 번 만으로 서버를 만들 수 있게 되었다.
- 하지만 버튼 클리고 역시 사람이 수동으로 하는 일이다.
- 인프라 자체를 코드로 선언하고, 반복 가능하게 만들고 싶다는 니즈가 발생!
    - Infrastructure as Code (IaC)의 개념이 확산되었다.

## 3. Terraform의 등장 ( 2014 )

- 2014년, HashiCopr에서 Terraform 0.1 공개!
- 특징
    - 인프라를 선언형으로 정의 ( Declaretive )
    - AWS, GCP, Azure 등 다양한 프로바이더 제공
    - 상태 관리 (terraform.tfstate) 를 통해서 실제 리소스와 코드 동기화
    - Immutable Infrastructure 지향하여 변경 대신 재생성 지향

## 4. Terraform vs 이전 도구들

|**항목**|**Terraform**|**Ansible/Chef/Puppet**|
|---|---|---|
|목적|인프라 생성 및 제거|서버 설정 및 애플리케이션 설치|
|접근 방식|선언형 (Declarative)|선언형 or 절차형|
|실행 대상|클라우드 API|OS 내부 (서버에 SSH 등 필요)|
|사용 시점|서버 **생성 전**|서버 **생성 후**|

## 5. 현재 : 표준 IaC 로 자리잡게 되었다!

|**가치**|**설명**|
|---|---|
|선언형 인프라|“무엇을 원한다”를 코드로 표현|
|멀티 클라우드 지원|AWS, Azure, GCP, 기타 SaaS까지 통합|
|상태 추적|.tfstate 파일로 실시간 인프라 상태 관리|
|변경 계획|terraform plan을 통해 변경 미리 확인|
|모듈화|반복되는 구성은 재사용 가능한 모듈로 작성|

## **✨ Terraform의 등장과 발전을 통해 얻는 교훈**

> “Terraform은
> 
> **복잡해진 클라우드 환경에서, 수동 운영과 스크립트 지옥을 벗어나기 위한 자연스러운 진화**

### Link of Thoughts
Area : #300-DevOps/340-Provisioning 

Keywords :
- 

Related Notes : 
- 