## Process & Thread 의 차이는? (만약 모르는 사람에게 비유를 들며 설명하자면)

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

- 생성: NEW 
- 실행가능: RUNNABLE (new Thread().start() 이후)
- 대기: WAIT
- 일정시간 대기: TIMED_WAIT
- LOCK이 풀리길 기다림: BLOCKED
- 종료: TERMINATED

- 실행: run() 이 호출되어 스레드가 cpu에 적재되어 실행중


### WAIT, TIMED_WAIT 차이
쓰레드가 TIME-WAITING 상태에 있다면 일정 시간이 지난후에서 다시 실행상태로 됩니다. 앞의 설명과 같이 잃어버린 monitor를 획득합니다.  
WAITING은 영원히 대기하며 쓰레드를 깨우기 전까지 실행되지 않습니다. Thread.join 메소드는 WAITING 상태로 들어가면 특정 쓰레드가 종료할 때까지 대기합니다.  
 

## 쓰레드풀이란? 왜쓰는지?

멀티쓰레드 환경에서, 메소드 호출 시 마다 스레드 생성 후 삭제하는 방식은 오버헤드가 큽니다. 
그래서 작업 큐에 작업들을 넣고, 작업별로 미리 생성된 스레드를 스레드풀로부터 작업에 할당하는 방식이 스레드 풀 입니다.  
일이 끝나면 쓰레드는 삭제되지 않고 다시 스레드풀에 반납됩니다.  

이를 통해 대규모서비스에서 스레드 생성 삭제 비용을 줄일 수 있습니다.  
다만, 너무 많이 생성하면 요청 수에 비해 쓰레드가 너무 놀아서 메모리 자원을 낭비하는 결과가 초래됩니다.  


## JDK thread pool 은 무엇이 있는지

ExecutorService?

## Executor, Future/Callable 의 개념과 역할
