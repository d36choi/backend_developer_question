## JVM, JRE, JDK ?

## 자바의 GC는 어떻게 동작하나요 ?


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
