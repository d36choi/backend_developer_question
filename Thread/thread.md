## Process & Thread 의 차이는?

Process : 실행된 프로그램이 메모리에 적재되어 실행중인 인스턴스
Thread : 프로세스의 흐름 단위

Process 가 피자 가게면, Thread 는 피자 굽는 직원, 배달하는 직원, 서빙하는 직원이라고 비유하고 싶다.  

Process 를 늘리면 가게에 필요한 가재도구를 똑같이 추가해야하지만 Thread 를 늘리면 직원들은 가전을 공유하는 대신 각자의 도구만 복제하면 된다. 
(스레드는 스택만 추가하고 힙과 전역데이터영역은 공유)

자바에서 하나의 프로세스는 하나의 메인 스레드를 지닌다.


## Thread 선언 시 사용하는 interface, class 는?
interface 는 `Runnable` 를 확장, class는 `Thread` 를 상속하여 쓰레드를 만듭니다. 
```java
// Runnable
public class Sample implements Runnable {...}

Thread t = new Thread(new Sample(i));
t.start();
```
interface를 선호하는 것이 일반적으로는 좋다고 보입니다. 왜냐하면 자바는 다중상속이 안되니까 Thread 를 상속하면 다른 클래스를 상속 못합니다.


## Thread 실행 메서드는?
 메서드를 구현하고 `new Thread(Runnable r).start();` 를 통해 스레드가 실행됩니다.
 start() 를 하면 해당 스레드 객체의 run() 을 호출합니다.



## Thread 선언 시 구현 메서드는?
둘다 `run()` 메서드에 동작하고자하는 로직을 구현하면 됩니다.



## Thread state 종류




### WAIT, TIMED_WAIT 차이



## 쓰레드풀이란? 왜쓰는지?



## JDK thread pool 은 무엇이 있는지



## Executor, Future/Callable 의 개념과 역할
