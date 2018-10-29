# 싱글턴 패턴

## 1. 프린터 관리자 만들기

- 한 부서에서 1개의 프린터를 공유해서 사용하기

- ```java
  public class User {
      private String name;
      
      public User(String name) {
          this.name = name;
      }
      
      public void print() {
          Printer printer = Printer.getPrinter();
          printer.print(this.name + "print using " + printer.toString() + ".");
      }
  }
  
  public class Printer {
      private static Printer printer = null;
      
      private Printer() {}
      
      public static Printer getPrinter() {
          if (printer == null) printer = new Printer();
          return printer;
      }
      
      public void print(String str) {
          System.out.println(str);
      }
  }
  
  public class Main {
      private static final int USER_NUM = 5;
      
      public static void main(String[] args) {
          User[] users = new User[USER_NUM];
          for (int i = 1; i < USER_NUM; i++) {
              users[i] = new User(i + "-user");
              users[i].print();
          }
      }
  }
  ```

## 2. 문제점

다중 스레드 개발 환경에서 문제점이 발생할 수 있다.

- 여러 스레드에서 Printer 클래스를 이용할 때 객체가 2개 이상 생성될 수 있다.
  - Printer 인스턴스가 아직 생성되지 않았을 때 Thread 1이 getPrinter 메소드의 if 문을 실행해 이미 인스턴스가 생성되었는지 확인한다. 현재 printer 변수는 null인 상태이다.
  - 만약 Thread 1이 생성자를 호출해 인스턴스를 만들기 전 Thread 2가 if 문을 실행해 printer 변수가 null인지 확인한다. 현재 null이므로 인스턴스를 생성하는 코드, 즉 생성자를 호출하는 코드를 실행하게 된다.
  - Thread 1도 Thread 2와 마찬가지로 인스턴스를 생성하는 코드를 실행하게 되면 결과적으로 Printer 클래스의 인스턴스가 2개 생성된다.
- Race condition : 한 자원(공유 데이터 등)을 2개 이상의 스레드가 이용하려고 경합하는 현상

## 3. 해결책

- 정적 변수에 인스턴스를 만들어 바로 초기화하는 방법

  - ```java
    public class Printer {
        private static Printer printer = new Printer();
        private int counter = 0;
        
        private Printer() {}
        
        public static Printer getPrinter() {
            return printer;
        }
        
        public void print(String str) {
            counter++;
            System.out.println(str);
        }
    }
    ```

- 인스턴스를 만드는 메소드를 동기화하는 방법

  - ```java
    public class Printer {
        private static Printer printer = null;
        private int counter = 0;
        
        private Printer() {}
        
        public synchronized static Printer getPrinter() {
            if (printer == null) printer = new Printer();
            return printer;
        }
        
        public void print(String str) {
            synchronized(this) {
                counter++;
            	System.out.println(str + counter);
            }
        }
    }
    ```

## 4. 싱글턴 패턴 : 단 하나의 인스턴스를 생성
