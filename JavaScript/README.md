[JavaScript]
======================

원래는 웹브라우저를 제어하기 위해 고안된 언어. (for ClientSide)  
현재는 다양한 분야에 응용이 가능하다.

# 1. ServerSide Script
```
웹 서버 (응답) -> 웹 <- (요청) 웹 브라우저
```
Node.js

# 2. ClientSide Script

## 2.1 jQuery

```HTML의 클라이언트 사이드 조작을 단순화 하도록 설계된 크로스 플랫폼의 자바스크립트 라이브러리.```

# 3. Grammar

## 3.1 비교 연산자 (==, ===)

### 3.1.1 동등 연산자 (==)

```다른 언어들과 마찬가지로 좌항과 우항을 비교해서 서로 값(value)이 같다면 true, 다르다면 false를 반환한다.```

### 3.1.2 일치(완전 항등) 연산자 (=== <=> !==)

```
다른 언어들과 다르게 자바스크립트에 존재하는 좌항과 우항이 정확하게 일치할 때 true, 다르다면 false를 반환하는 연산자
정확하게 일치한다는 의미는 값(value)뿐만이 아니라 데이터형까지 엄격하게 일치해야 한다는 것이다.
```

## 3.2 Data Type

1. null - 프로그래머가 의도한 값이 없는 상태  
2. undefined - 말 그대로 정의되지 않은, 그래서 값이 없는 상태를 말한다.
3. NaN - 불가능한 연산의 결과를 반환 (ex. x / 0 등등)
4. boolean - true / false (* '' == false, 'string', !undefined, !null, !NaN == true)

## 3.3 Regular Expression (정규 표현식)

## 3.4 Debug

> Chrome 개발자 도구 (F12) - Sources 탭을 통해 디버깅이 가능하다. (Go to next breakpoint, Step into, Step over)  
	=> Watch Expressions : 변수를 입력하면 해당 변수에 대한 모니터링이 가능.  
	=> Global : 전역 변수  
	=> Scope Variables : 지역 변수  
	=> 스크립트 코드 중단점 외에도 DOM, XHR, Event Listener 중단점도 있다.