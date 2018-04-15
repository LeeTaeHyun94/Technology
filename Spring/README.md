# Spring Framework

## 1. AOP (Aspect Oriented Programming)

Business Logic은 아니지만 반드시 해야하는 공통된 작업을 Aspect라고 한다.

```
- Aspect : 공통 관심사에 대한 추상적인 명칭 (ex : logging, security, transaction...)  
	- Before Advice : Target의 메소드 호출 전에 적용  
	- After Returning : Target의 메소드 호출 이후에 적용  
	- After Throwing : Target의 예외 발생 후에 적용  
	- After : Target의 메소드 호출 후, 예외의 발생에 관계없이 적용  
	- Around : Target의 메소드 호출 전후 모두 적용
- Advice : 실제 기능을 구현한 걕체 (클래스를 제작하고 @Advice를 적용)
- Join Points : 공통 관심사를 적용할 수 있는 대상. (Spring AOP에서는 각 객체의 메소드가 해당)
- Pointcuts : 실제 Advice가 적용될 메소드
- Target : 대상 메소드를 가지는 객체 (실제 비즈니스 로직을 수행하는 객체)
- Proxy : Advice가 적용되어 만들어지는 걕체
- Introduction : Target에 없는 새로운 메소드나 인스턴스 변수를 추가하는 기능
- Weaving : Advice와 Target이 결합되어 Proxy 객체를 만드는 과정
```



## 2. MVC 패턴 특화



## 3. Developing Process



### 3.1 등록, 수정, 삭제, 조회 기능의 구현



### 3.2 Persistence, Business layer implementation

* root-context.xml, ~mapper.xml, ~DAOImpl.class 파일들의 mapping 경로를 확인해야 한다. (수시로 JUnit Test.)



### 3.3 등록 구현 - Controller, Presentation layer implementation



## 4. Ajax를 통한 댓글 처리

* Representational State Transfer : 하나의 URI는 하나의 고유한 Resource를 대표하도록 설계된다는 개념  
최근에는 서버에 접근하는 기기의 종류가 다양해서 다양한 기기에서 공통으로 데이터를 처리할 수 있는 규칙을 만드는 방식.

* REST API : 특정 URI를 통해서 사용자가 원하는 정보를 REST 방식으로 제공하는 외부 연결 URI

```
스프링에서는 @RestController 어노테이션을 이용하여 RESTful하게 구현
REST 방식이 데이터를 호출하고 사용하는 방식을 의미한다면 Ajax는 그를 이용하는 수단.
```

- Asynchronous JavaScript and XML (Ajax) : 대화형으로 서버와 데이터를 주고받는 형태의 전송 방식  
  데이터를 요청하고 기다리지 않는 것이 특징, 화면 전환이나 깜빡임 없이 데이터를 받기 때문에 UX 측면에서 좋다.



## 5. Transaction

하나의 업무에 여러 개의 작은 없무들이 같이 묶여 있는 것.

(ex. (게시글 추가, 포인트 적립), (댓글 추가, 댓글 숫자 업데이트))

* DB의 정규화와 트랜잭션은 서로 연관이 깊다. (정규화가 잘 돼 있을수록 연관 있는 데이터가 줄어들어 트랜잭션의 처리 또한 줄어든다.)
* Atomicity (원자성 - 트랜잭션은 하나의 단위로 처리), Consistency (일관성), Isolation (격리), Durability (영속성)

### 5.1 @Transactional

* Method > Class > Interface 순으로 트랜잭션 어노테이션 설정이 우선시된다.

