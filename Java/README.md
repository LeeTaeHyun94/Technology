[Java]
======================

# 1. Java의 실행 과정

자바 프로그램(.java)을 클래스 파일(.class)로 컴파일 (Byte Code 생성)하여 JVM 명령으로 변환하여 JVM에서는 JIT 컴파일을 통해 기계어로 컴파일한다.

- 실행 환경에 따라 별도의 컴파일을 하지 않아도 모든 실행 환경에서 JVM만 있다면 실행할 수 있게 하기 위함.
- JIT Compile (Just-In-Time Compile) : 프로그램을 실제 실행하는 시점에 기계어로 번역하는 컴파일 기법


# 2. Grammar

## 2.1 입출력

### 2.1.1 출력
```System.out.println();```
```
* Console에서의 출력은 java.lang 패키지에 있는 System 클래스에 접근하여 Console을 타깃으로 하는 PrintStream 객체로  
    선언한 정적 변수 out을 통해 println() 메소드 호출  
	out : 표준 출력 메소드를 갖고 있는 추상 클래스 OutputStream을 상속받아 FilterOutputStream 클래스에서  
	    필터링을 거치고 상속받은 PrintStream 객체
```

### 2.1.2 입력
```
Scanner input = new Scanner(System.in);
input.next...();
```

```
* java.util 패키지를 참조하여 Scanner 객체 이용  
	in : 출력과 마찬가지로 System 클래스에 선언되어 있는 정적 변수 in
	     표준 입력 메소드를 갖고 있는 추상 클래스 InputStream을 상속받은 PrintStream 객체
```

## 2.2 클래스, 객체와 인스턴스

1. 클래스 : 구현할 대상의 설계도
2. 객체 : 구현할 대상
3. 인스턴스 : 구현된 실체 (객체에 해당하는 인스턴스의 메모리를 힙 영역에 할당하고 객체는 이 힙 영역의 메모리를 가리킨다. 이를 인스턴스화라고 한다.)

## 2.3 자료형과 클래스
```Java에서는 변수를 클래스 형태로 선언이 가능하다. 기본 자료형의 첫 문자를 대문자로 쓰면 된다. 이를 통해 클래스로서 변수를 관리하면 변수를 통해 관련 메소드들을 사용 가능하다는 장점이 있다.```

## 2.4 Garbage Collection

Java는 프로그램 코드 내부에서 메모리를 명시적으로 직접 해제하지 않는다. 때문에 Garbage Collector가 더 이상 필요없는 사용되지 않는 객체를 찾아 지우는 작업을 한다.  
stop-the-world 이후에 Garbage Collection 작업을 완료한다. 때문에 Java를 이용해 개발하게 된다면 프로그램의 성능을 높이기 위해서는 직접 Java의 Garbage Collection 상황을 모니터링해 튜닝이 필요하다.  

* stop-the-world : JVM이 애플리케이션을 실행 중지하는 것을 말한다. Garbage Collection을 실행하는 쓰레드 외에 나머지 쓰레드는 모두 작업을 멈추게 된다.  
* Garbage Collector가 더 이상 필요없는 객체를 찾는 알고리즘
  * Young Generation 영역 : 새롭게 생성한 객체의 대부분이 이 영역에 위치한다.
    * 대부분의 객체가 금방 접근 불가 상태가 되기 때문에 매우 많은 객체가 이 영역에 생성되었다가 사라진다.
    * 이 영역에서 객체가 사라질 때 Minor GC가 발생한다고 한다.
    * Eden 영역과 2개의 Survivor 영역으로 나뉜다.
      * 새로 생성한 대부분의 객체는 Eden 영역에 위치
      * Eden 영역에서 GC가 한 번 발생한 후 살아남은 객체는 Survivor 영역 중 하나로 이동
      * Eden 영역에서 GC가 발생하면 살아남아 있는 객체가 존재하는 Survivor영역으로 객체가 계속 쌓인다.
      * 하나의 Survivor영역이 가득 차게 되면 그 중에서 살아남은 객체를 다른 Survivor 영역으로 이동
      * 가득 차 있던 Survivor 영역은 빈 상태가 된다.
      * 위 과정을 반복하다가 계속해서 살아남아 있는 객체는 Old 영역으로 이동된다.
      * Survivor 영역 중 하나는 반드시 빈 상태여야 한다. 만약에 그렇지 않다면 시스템 상태가 비정상이라는 것
  * Old Generation 영역 : 접근 불가능 상태로 되지 않아 Young 영역에서 살아남은 객체가 이 영역으로 복사된다.
    * 대부분 Young 영역보다 크게 할당하며, 크기가 큰 만큼 Young 영역보다 GC는 적게 발생한다.
    * 이 영역에서 객체가 사라질 때 Major GC가 발생한다고 한다.
    * Old 영역의 기본적으로 데이터가 가득 차면 GC를 실행한다.
    * JDK 7 기준 5가지의 GC 방식이 있다.
      * Serial GC
        * Old 영역의 GC는 mark-sweep-compact 알고리즘을 사용한다.
          - Old 영역의 살아 있는 객체를 식별(Mark)
          - 힙의 앞 부분부터 확인하여 살아 있는 것만 남긴다.(Sweep)
          - 각 객체들이 연속되게 쌓이도록 힙의 가장 앞 부분부터 채워서 객체가 있는 부분과 없는 부분으로 나눈다.(Compaction)
        * 메모리가 적고 싱글 코어일 때 적합한 방식
      * Parallel GC
        * 기본적인 알고리즘은 Serial GC와 같다.
        * GC를 처리할 때 다수의 스레드를 이용하기 때문에 Serial GC보다 빠르게 처리할 수 있다.
        * 메모리가 충분하고 코어의 개수가 많을 때 유리하다.
        * Throughput GC라고도 한다.
        * ![Difference in (Serial GC & Parallel CG)](./img/4.PNG)
      * Parallel Old GC
        * JDK 5 update 6부터 제공한 GC 방식
        * Parallel GC와 Old 영역의 GC 알고리즘만 다르다.
        * Mark-Summary-Compaction 알고리즘을 사용
          * 앞서 GC를 수행한 영역에 대해서 별도로 살아 있는 객체를 식별(Summary)
      * Concurrent Mark & Sweep GC
        * Initial Mark 단계 : ClassLoader에서 가장 가까운 객체 중 살아 있는 객체만 찾는다.
        * Concurrent Mark 단계 : 살아있음을 확인한 객체에서 참조하고 있는 객체들을 따라가면서 확인, 다른 스레드가 실행 중인 상태에서 동시에 진행된다.
        * Remark 단계 : Concurrent Mark 단계에서 새로 추가되거나 참조가 끊긴 객체를 확인
        * Concurrent Sweep 단계 : 쓰레기 정리, 다른 스레드가 실행 중인 상태에서 동시 진행
        * stop-the-world 시간(멈추는 시간)이 매우 짧다.
        * 애플리케이션의 응답 속도가 매우 중요할 때 사용하며, Low Latency GC라고도 부른다.
        * 다른 GC 방식보다 메모리와 CPU를 많이 사용한다.
        * Compaction 단계가 기본적으로 제공되지 않기 떄문에 조각난 메모리가 많아 Compaction 작업 시에 stop-the-world 시간이 다른 GC 방식보다 길기 때문에 Compaction 작업에 대한 모니터링이 필요하다.
        * ![Concurrent Mark & Sweep GC](./img/5.PNG)

      * Garbage First(G1) GC
        * 바둑판의 각 영역에 객체를 할당하고 GC를 실행한다.
        * 해당 영역이 꽉 차면 다른 영역에서 객체를 할당하고 GC를 실행한다.
        * 다른 방식에 적용된 Young, Old 영역의 개념이 없다.
        * 이전의 GC 방식들보다 빠르다.
        * ![Garbage First GC](./img/6.PNG)
  * 영역 별 데이터 흐름
    * ![Garbage Collector Data Flow](./img/1.PNG)
    * ![Garbage Collector Data Flow](./img/3.PNG)
  * Permanent Generation 영역 : Method Area라고도 한다. 객체나 억류(intern)된 문자열 정보를 저장하는 곳

    * 이 영역에서 GC가 발생해도 Major GC의 횟수에 포함된다.
  * Old 영역의 객체가 Young 영역의 객체를 참조하는 경우
    * Old 영역에는 512 byte의 덩어리(chunk)로 되어 있는 card table이 존재한다.
    * 이 Card table을 통해 Old 영역의 객체가 Young 영역의 객체를 참조할 때마다 정보를 표시한다.
    * Young 영역의 GC를 실행할 때에는 Old 영역에 있는 모든 객체의 참조를 확인하는 것이 아니라 이 Card table만 탐색해서 GC 대상인지 식별한다.
    * ![Card table](./img/2.PNG)
    * Card table은 Write Barrier를 사용하여 관리한다.
      * Write Barrier : Minor GC를 빠르게 할 수 있도록 하는 장치
        * 약간의 오버헤드는 발생하지만 전반적인 GC 시간은 감소

# 3. Object-Oriented Programming - 객체지향에 대한 이해

```
'객체'라는 여러 개의 독립된 단위들의 모임을 중점으로 하는 프로그래밍 패러다임.
기존의 절차 지향 프로그래밍의 단점을 보완하기 위해 데이터와 함수를 하나의 덩어리(객체)로 묶어서 생각하게 되었다.
 * 절차 지향 프로그래밍의 단점 : 함수 작성에만 신경 쓰게 되고 전역 변수가 과도하게 사용되어 데이터가 함수와 분리된다.  
    그로 인해 프로그램의 이해가 어려워지고 차후에 변경하거나 확장하기 어려워진다.

```
- 장점 : 프로그램이 유연하다. 이는 변경하기 용이하다는 말과 상통한다. 간편한 소프트웨어 개발 및 보수, 보다 직관적인 코드 분석이 가능.    
	 소프트웨어 공학의 관점에서 볼 때 S/W의 질을 향상하기 위해 강한 응집력(Strong Cohesion)과 약한 결합력(Weak Coupling)을 지향해야 하는데,    
	 OOP의 경우 클래스에 하나의 문제 해결을 위한 데이터를 모아 놓은 데이터형을 사용함으로써 응집력을 강화하고, 클래스간에 독립적으로 디자인함으로써 결합력을 약하게 할 수 있다.

- 특징 : 캡슐화(<=정보은닉), 추상화, (다중)상속, 다형성, 동적 바인딩
