---
aliases:
  - Docker
tags:
  - 완료
  - 문헌메모
---



---


Source :
Author : 
URL :

### Docker 란?
* Docker는 컨테이너 기술을 사용하여 애플리케이션에 필요한 환경을 신속하게 구축하고 테스트 및 배포를 할 수 있게 해주는 플랫폼 이다.
> Platform
> * Linux
>   * Ubuntu
>   * CentOS
>   * Debian
> * Cloud
>   * AWS
>   * Azure   


※ Docker가 컨테이너 기술을 만든 것이 아닌, 컨테이너 기술을 사용하기 쉽게 만든 프로그램 이다.


### Container 란?
* Host OS 상에서 리소스를 논리적으로 구분하여 마치 별도의 서버인 것 처럼 사용할 수 있게 하는 기술

* 사용 이유
  * 이식성과 확장성이 좋다
    * 컨테이너 이미지 그대로 의존성 없이 다른 환경에서 실행 가능
    * 컨테이너를 여러 개 실행해서 이중화 가능
 
### Docker 이미지
* 컨테이너를 생성하는 베이스가 되는 것
* 클래스와 객체의 개념이랑 비슷함
* 단순히 개발하고 있는 애플리케이션만 이미지로 만들고 배포하는것이 아니라, Database나 WAS 처럼 미들웨어로 사용되는 프로그램들도 Docker Hub에 배포되어 있기 때문에 받아서 사용하면 된다.
> * Mysql 이미지를 받아서 컨테이너를 생성하고 DB로 활용
> * Java, Apache/Tomcat이 설치되어 있는 이미지를 받아서 그 위에 애플리케이션을 올리고 재배포


### 개발과 배포의 흐름
* Docker를 사용해서 서비스를 운영한다는 것은 애플리케이션들을 컨테이너화 했다는 뜻입니다
![스크린샷 2023-05-28 오후 4 09 53](https://github.com/HyunSu1768/TIL/assets/108796235/74c3be07-c81b-4861-acd3-afe54a6e6fa3)
> 1. 개발자가 개인 PC에서 Docker 이미지를 빌드해서 Repository에 배포한다.
> 2. 테스트, 스테이징, 프로덕션 환경에 Docker 프로그램만 설치하고 배포된 애플리케이션 이미지를 받아 실행 후 테스트 한다.


### Link of Thoughts
Area : #300-DevOps/320-Container-Orchestration 

Keywords :
- [[Docker]]

Related Notes : 
- [[Host OS란?]]