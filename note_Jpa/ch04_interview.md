![image-20211201214251665](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20211201214251665.png)

- @Entity 
  - 해당 클래스를 테이블과 매핑한다고 JPA에 알려준다. (JPA가 해당 클래스를 관리하게 된다.)
  - **즉, 엔티티 클래스임을 말해준다**

- Entity

  - 어떤 **인스턴스의 집합**이다.
  - 개별 인스턴스는 속성을 지닌다.

  

- final

  - 지연 로딩 방식을 이용하기 때문 **(솔직히 이해 잘 안감)**
    - 정의 : 해당 엔티티(테이블)와 관계(join)를 맺고 있는 엔티티(테이블)들에 대한 정보는 그 즉시 로딩되지 않고 getter 메소드가 호출되는 등 실제 사용될 때 로딩된다. 이러한 방식을 지연 로딩이라 한다
    - 작동 방식 : JPA가 프록시 객체 생성
      - 프록시 객체 = 엔티티 클래스를 상속해서 확장한 클래스인데, 
      - final class는 상속 불가능하기 때문에, 엔티티 클래스로 사용 불가능



---

![image-20211201214310261](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20211201214310261.png)

이 DDL이 실행되지 못한 이유는?

- 예약어가 사용되어서 그런 것 같다
  - 아마 name..? -> 실험해보니까 name 예약어 아닌데...
- String 컬럼에 @GeneratedValue(strategy = GenerationType.IDENTITY) 를 적용한 것이 문제
  - DB에 ID생성 전략이 위임되어, String id에 AI 가 적용되는데, string에는 ai가 적용될 수 없기 때문에 오류가 생긴다.



---

![image-20211201214332178](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20211201214332178.png)

- DATE
  - YYYY-MM-DD
- TIME
  - HH:MM:SS
- DATETIME
  - YYYY-MM-DD HH:MM:SS
  - 문자형
- TIMESTAMP
  - 1970-01-01 00:00:01 ~ 2038-01-01 03:14:07
  - 숫자형
  - 값 입력 안하면,  자동으로 현재 날짜&시간 입력됨
- datetime vs timestamp
  - datetime :
    - 문자형
    - 타임존이 바뀌어도 값이 변하지 않는다
    - 국내용으로 사용

  - timestamp
    - 숫자형
    - 타임존이 바뀌면, 해당 타임존에 맞게 시간 값이 바뀐다.
    - 국제용으로 사용


---

참고로 자바의 날짜 형식은 다음과 같다

- DATE
  - **시, 분, 초 다 존재**



따라서, **@Temporal 을 사용하여 [자바 -> DB] 날짜형식으로 매핑**하는 것이다.

- @Temporal 생략 시, DATE 와 가장 유사한 TIMESTAMP 형식으로 매핑
- mysql에서는, **DATE -> DATETIME** 으로 매핑된다.

---