# Spring Framework

## 1.1 AOP (Aspect Oriented Programming)

## 1.2 MVC 패턴 특화

## 1.3 Developing Process

### 1.3.1 등록, 수정, 삭제, 조회 기능의 구현

### 1.3.2 Persistence, Business layer implementation

* root-context.xml, ~mapper.xml, ~DAOImpl.class 파일들의 mapping 경로를 확인해야 한다. (수시로 JUnit Test.)

### 1.3.3 등록 구현 - Controller, Presentation layer implementation

## 1.4 Ajax를 통한 댓글 처리

* Representational State Transfer : 하나의 URI는 하나의 고유한 Resource를 대표하도록 설계된다는 개념  
최근에는 서버에 접근하는 기기의 종류가 다양해서 다양한 기기에서 공통으로 데이터를 처리할 수 있는 규칙을 만드는 방식.

* REST API : 특정 URI를 통해서 사용자가 원하는 정보를 REST 방식으로 제공하는 외부 연결 URI

```
스프링에서는 @RestController 어노테이션을 이용하여 RESTful하게 구현
REST 방식이 데이터를 호출하고 사용하는 방식을 의미한다면 Ajax는 그를 이용하는 수단.
```

- Asynchronous JavaScript and XML (Ajax) : 대화형으로 서버와 데이터를 주고받는 형태의 전송 방식  
데이터를 요청하고 기다리지 않는 것이 특징, 화면 전환이나 깜빡임 없이 데이터를 받기 때문에 UX 측면에서 좋다.
