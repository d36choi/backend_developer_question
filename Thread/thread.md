## Process & Thread 의 차이는?




## Thread 선언 시 사용하는 interface, class 는?
interface 는 `Runnable` 를 확장, class는 `Thread` 를 상속하여 쓰레드를 만듭니다. 



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
