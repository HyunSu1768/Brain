# 영속성 컨텍스트

<aside>
💡 JPA에서 가장 중요한 2가지

---

- 객체와 관계형 데이터베이스 매핑하기 (Object Relational Mapping)
- **영속성 컨텍스트**
</aside>

<aside>
💡 영속성 컨텍스트!

---

- JPA를 이해하는데 가장 중요한 용어이다.
- “엔티티를 영구 저장하는 환경”
- EntityManager.persist(entity);

<aside>
💡 엔티티 매니저와 영속성 컨텍스트

---

- 영속성 컨텍스트는 논리적인 개념이며 눈에 보이지 않느다.
- 엔티티 매니저를 통해서 영속성 컨텍스트에 접근한다.
</aside>

</aside>

<aside>
💡 엔티티의 생명주기

---

- 비영속 (new/transient)
    - 영속성 컨텍스트와 전혀 관계가 없는 새로운 상태이다.
- 영속 (managed)
    - 영속성 컨텍스트에 관리되는 상태이다.
- 준영속 (detached)
    - 영속성 컨텍스트에 저장되었다가 분리된 상태이다.
- 삭제 (removed)

![Screen Shot 2023-04-12 at 5.14.10 PM.png](%E1%84%8B%E1%85%A7%E1%86%BC%E1%84%89%E1%85%A9%E1%86%A8%E1%84%89%E1%85%A5%E1%86%BC%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%86%A8%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%203b60768a72134e2cab500c402a8c34ce/Screen_Shot_2023-04-12_at_5.14.10_PM.png)

</aside>

<aside>
💡 영속

---

```java
Member member = new Member();
member.setId("member1");
member.setUsername("회원");

EntityManager em = emf.createEntityManager();
em.getTransaction().begin();

em.persis(member); // 객체를 저장한 상태(영속)
```

</aside>

<aside>
💡 비영속

---

```java
Member member = new Member();
member.setId("member1");
member.setUsername("회원");
```

</aside>

<aside>
💡 준영속, 삭제

---

```java
//회원 엔티티를 영속성 컨텍스트에서 분리, 준영속 상태
em.detach(member);

//객체를 삭제한 상태(삭제)
em.remove(member);
```

</aside>