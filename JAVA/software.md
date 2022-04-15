## JVM, JRE, JDK ?

현실세계와 비유하자면, JVM = 컴퓨터, JRE = OS, JDK = 소프트웨어 개발 도구  
JVM < JRE < JDK 순으로 포함합니다.  
JVM : 자바 파일에서 변환된 클래스파일을 OS별로 동일하게 실행시킬 수 있도록 합니다. **GC**, **런타임 데이터 영역**(aka. JVM memory 영역)을 가지고 있습니다. 우리가  
실행환경에 따라 코드를 바꾸지 않아도 되는 이유가 JVM 은 설치된 OS별로 맞는 환경을 클래스코드에 제공하기 때문입니다.  
JRE : **JVM 이 바이트 코드 실행시 필요로 하는 라이브러리**를 포함하고 있습니다. (java.io , java.util , java.thread)  
JDK : 컴파일러인 **javac** 랑 디버거인 **jdb**, **javadoc** 등이 포함되어있습니다. 널리 쓰이는건 LTS버전인 jdk 8과 11입니다. 

## JDK Runtime Data Area의 내부 구조를 설명해보세요.
JDK 메모리 영역은 **스택, 힙, 메소드영역, PC 레지스터**등으로 구성됩니다.

- 메소드 : 클래스 인스턴스 생성 위해 필요한 코드들, 상수풀을 가지고 있고 모든 스레드가 공유합니다. 프로그램 구동 시작부터 끝까지 남아있습니다.
- 스택 : 현재 실행 중인 메서드 프레임과 지역 변수와 참조 변수들을 푸쉬해 쌓고 메서드가 실행종료되면 pop하여 그 밑에 쌓인 메서드의 위치로 돌아갑니다. 스레드 별로 할당됩니다.
- 힙 : 동적으로 생성된 인스턴스들이 저장되는 공간입니다. 스택변수들이 참조하는 실제 값들이고 GC에 의해 소멸이 관리가 됩니다. 스레드별로 공유되기 때문에 문제가 생기지않게 관리해야 합니다.

## 자바의 GC는 어떻게 동작하나요 ?
GC 는 여러 영역으로 나뉩니다. 크게는 Young Generation, Old Generation 으로 나뉩니다. 각각의 장소에서 일어나는 GC를 minor, major gc 라고 합니다.
young 에서는 새로 생성된 객체들이 들어가게 되고, 금방 어디서도 참조하지 않는 객체들이 많기 때문에 많은 GC가 발생합니다.  
old 에는 young에서 살아남은 객체들이 이동을 하게 되고 자주 발생하지 않습니다. 
- young : Eden, survivor0, survivor1 로 구성. 새로 생성된 객체는 Eden 에 가고 살아남으면 survivor로 이동. survivor 가 하나가 꽉차면 다른 하나로
모두 이동시킵니다. 말하자면 둘 중 하나는 꼭 비어있어야 합니다.
- old : ?

### GC 를 알아야 하는 이유는?
우리 개발자들은 명시적으로 힙영역에서 객체의 소멸을 관리하지 않는다. GC가 해주는데, GC 가 실행될 때에는 stop-the-world 즉, 모든 쓰레드가 동작을 멈춘다.
그렇기 때문에 GC 가 길어지면 시스템에 큰 영향을 끼치게 되므로 개발자는 GC 튜닝 및 관리를 통해 문제를 해결할 줄 알아야 하기 때문입니다.

## java string constant pool 이란?

자바에서 문자열 String은 불변객체이기 때문에 가능한 메모리 구조입니다. 자바7때부터 HEAP 영역에 String Pool 이 옮겨졌고, 반복되는 문자열 리터럴을 재사용할 수 있게 해줍니다.
<img width="715" alt="image" src="https://user-images.githubusercontent.com/40600306/163512842-f41dd875-1127-46b2-bc99-b5f3556ff648.png">


## java 는 call by value 인가 call by reference 인가?

call by value다. 
자바는 객체(참조 타입)을 메서드로 넘길 때 참조하는 지역변수의 실제 주소를 넘기는 것이 아니라 그 지역변수가 가리키고 있는 힙 영역의 객체를 가리키는 새로운 지역변수를 생성하여 
그것을 통하여 같은 객체를 가리키도록 하는 방식임을 알 수 있다.
또한 새로운 지역변수를 생성해 이루어지기 때문에 기본 타입을 매개변수로 받아 값을 바꾼 경우와 참조타입을 매개변수로 받아 값을 변경한 경우 모두 스택에서 변경이 이루어지기 때문에 아무런 의미가 없게 된다.

- 메서드로 넘겨간 객체의 주소를 넘겨주는게 아니라 **스택에서 생성된 지역 변수에 의해 같은 객체를 바라보게 되는 것이다**
```java
public class MyClass {
    public static void main(String args[]) {
      cbr();
    }
    public static void cbr() {

        final Money money1 = new Money(3000);
        final Money money2 = new Money(5000);
        swap(money1, money2);
        System.out.println(money1.amount - money2.amount);
    }

    public static void swap(Money money1, Money money2) {
        Money temp = money1;
        money1 = money2;
        money2 = temp;

    }

    public static class Money {
        public int amount;

        Money(int amount) {
            this.amount = amount;
        }

    }
}
```

## JVM Stack 과 Heap의 차이는?
Stack 에는 실행 메서드의 로컬 변수, Heap 에 저장된 객체의 주소를 참조하는 참조 변수, 인자 등이 포함된다.
메서드 실행이 종료된 해당 메서드에서 사용된 변수들은 모두 POP된다.
  
Heap은 모든 Object class 들의 인스턴스가 저장된다. 주로 서로 다른 영역에서 참조되는 데이터들이 들어간다.
Garbage Collection 을 통해 해당 객체들을 참조하는 변수가 없다면은 메모리의 삭제가 이루어진다.

  
