---
aliases:
  - Linux
tags:
  - 문헌메모
  - 완료
---


---


Source :
Author : 
URL :

## Page Fault란?
1. 정의 : Page Fault란 현재 프로세스가 접근하려고 하는 페이지가 실제 물리 메모리에 존재하지 않을때 발생하는 예외
2. 목적 : Page Fault 매커니즘은 프로세스가 필요로 하는 페이지를 효율적으로 로드하고 관리하는데 도움이 된다. Page Fault를 사용함으로서 기존 메모리의 크기보다 더 큰 가상 메모리 공간을 사용할 수 있다.

## Page Fault 작동방식
1. Page Fault 발생 : 프로세스가 메모리에 접근할 때, 가상 주소로 되어있는 페이지가 물리적 메모리에 존재하지 않으면 Page Fault가 발생한다.
2. 인터럽트 처리 : Page Fault는 운영체제에 의해 관리되는 인터럽트 이다. Page Fault 인터럽트가 발생되면 CPU의 상태를 저장한 뒤 Page Fault 인터럽트 처리 루틴을 실행한다.
3. 페이지 로딩 : 운영 체제는 필요한 페이지를 물리 메모리에 로드한다. 이 페이지는 스왑 영역이나 해당 파일 시스템에서 가져올 수 있다.
4. 페이지 테이블 업데이트 : 페이지가 메모리에 로드된 후, 기존 페이지 테이블을 새로운 주소와 함께 업데이트한다.
5. 프로세스 재게 : 페이지 로딩이 완료되면, CPU는 프로세스를 재게한다.

## Page Fault의 유형
1. Minor Page Fault
	- Minor Page Fault는 페이지가 메모리 내에 존재하지만, 페이지 테이블에 매핑되지 않았을때 발생
2. Major Page Fault
	- 페이지가 물리적 메모리에 존재하지 않고, 디스크에서 로드해야할 때 발생, 더 많은 시간이 소요됨

### Link of Thoughts
Area : #300-DevOps/330-Operating-System 

Keywords :
- [[Linux]]

Related Notes : 
- [[Page란?]]