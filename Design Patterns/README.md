## Architectural Design Patterns

# MVC 패턴 (Model + View + Controller)
 1) Model : 프로그램에서 사용되는 데이터와 데이터를 조작하는 로직을 처리
 2) View : 사용자에게 제공되는 UI(User Interface), 보여지는 부분
 3) Controller : 사용자의 입력과 동작을 받고 입력에 맞게 Model에 반영, 동작에 맞게 Model을 참조하여 로직에 맞게 처리
 -> 장점 : 유연성, 확장성이 높다.
	   View와 Model 간의 간섭을 피하고 Controller가 중간 관리 역할을 하여 간접연결을 통해 유연한 구조를 설계 가능하다.
    단점 : View와 Model이 서로 의존적이다. 의존성이 높다는 것은 Model과 View의 완벽한 분리가 어렵다는 뜻이다. 이는 패턴이 모호해질 수 있으며 변형을 초래할 수 있다.

# MVP 패턴 (Model + View + Presenter)
 1) Model : 프로그램에서 사용되는 데이터와 데이터를 조작하는 로직을 처리
 2) View : 사용자에게 제공되는 UI(User Interface), 보여지는 부분
 3) Presenter : View에서 요청한 정보를 Model에서 가공해서 전달
 -> 장점 : View와 Model의 의존성을 제거하여 완벽하게 분리한다. 동시에 MVC 패턴의 장점 또한 갖고 있다.
    단점 : View와 Presenter가 1:1로 강한 의존성을 갖는다. MVC 패턴과 비슷하게 Model과 Presenter의 완벽한 분리가 어렵다는 뜻이다.

# MVVM 패턴
 1) Model : 프로그램에서 사용되는 데이터
 2) View : 사용자에게 제공되는 UI(User Interface), 보여지는 부분
 3) ViewModel : View를 표현하기 위한 Model, Command를 통해 로직을 수행하고 데이터를 처리하여 Model에 저장
 동작 패턴(Behavioral Patterns)에 속하는 Command 패턴과 동시성 패턴(Concurrency Patterns)에 속하는 Binding Properties 패턴을 이용하여
 View를 통해 입력이 들어오면 Command를 통해 ViewModel에 명령이 내려지고 Data Binding으로 인해 ViewModel의 값(정확히는 Model에서 받아온 데이터)이 변화하면 View의 정보가 동시에 바뀌게 된다.
 -> 장점 : 기존 MVP 패턴이 갖고 있던 View와 Presenter의 1:1 의존성을 Command 패턴과 Binding Properties 패턴을 통해 View와 ViewModel로 구성하여 두 부분의 의존성을 제거함.
    단점 : View와 Presenter가 1:1로 강한 의존성을 갖는다. MVC 패턴과 비슷하게 Model과 Presenter의 완벽한 분리가 어렵다는 뜻이다.
