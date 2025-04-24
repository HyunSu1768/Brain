---
aliases:
  - Cloudflare
tags:
  - 문헌메모
  - 완료
---


---


Source : Liner Deep Research
Author : 
URL :

## Cloudflare Tunnel의 터널 연결 방식
![[Pasted image 20250424140959.png]]
Cloudflare Tunnel은 내부 서버에 cloudflare daemon (cloudflared) 를 실행시키고, Cloudflare 네트워크와 여러개의 아웃바운드 커넥션을 맺는다. (보통 4개 이상). 이러한 연결들을 고가용성을 제공한다. 내부 서버에서 발생하는 트래픽은 cloudflared에 의해 암호화, 캡슐화 되고 Cloudflare Network까지 안전하게 전송된다.

외부 사용자가 도메인에 접근하면 Cloudflare Network 에 전달되고 보안검사를 거친 뒤 Tunnel을 통해 원본 서버로 전달된다. 반대로 응답 또한 Tunnel을 통해 Cloudflare Network 로 전달되고 보안 검사를 마친 뒤 사용자에게 전달된다.

### Link of Thoughts
Area : #300-DevOps/310-Cloud-Flatform 

Keywords :
- 

Related Notes : 
- [[Cloudflare Tunnel의 기본 개념과 역할]]