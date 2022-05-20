
## interface 와 abstract가 어떻게 다른지 설명해주세요

메서드의 구현여부다. 메서드나 하나라도 구현되어있다면 (내용이 정의된 케이스가 있다면)

abstract 여야 한다.

### abstract class 는 왜쓸까요?

확장되는 클래스들이 많은데, 특정 메서드는 무조건 구현되어야하면서

메서드들이 각자 별도의 내용으로 구현되어야한다면 추상클래스로 만들어놓으면 좋다.

### interface는 왜 쓸까요?

클래스 추상화 과정에서 공통된 행위를 갖는 표준을 선언한다.

### final class는 언제쓸까요?

더이상 확장 불가, 자식을 가질 수 없는 클래스다. String이 그러하다.

### default method는?

java 8 도입. 하위 호환성을 위해 도입되었고 interface에 내용을 포함한다.

## abstract class 와 일반 class의 다른점은?

추상 클래스는 new 키워드로 인스턴스 생성이 단독으로 불가능하고 확장된 서브클래스가 있어야 가능하다.

추상 클래스는 하위 클래스들의 기능 구현을 강제할 수가 있다. 이 클래스를 상속받는 하위 클래스들은 무조건 

abstract method를 구현해야만 일반 클래스로 정의가 가능하기 때문이다.

## overloading 과 overriding 의 차이와 예시를 설명하라
둘다 자바의 다형성을 위한 키워드입니다.
오버로딩은 메서드 이름이 같지만 인자와 ~~리턴 자료형이 다른~~ 메서드를 다중 정의
오버라이딩은 상위클래스의 메서드를 하위 클래스에서 재정의 하는 것을 의미합니다.



## 왜 `Map<Integer,String> doc = new HashMap<>();`라고 쓰는지?
  클래스를 다양한 타입에 적용시켜 재사용할 수 있도록 해주는 제네릭 타입때문입니다.  
  여러가지 장점이 있으며 대표적으로 타입캐스팅을 하지 않아도 되고 컴파일타임에 자료형 에러를 알려주는 등의 기능이 있습니다.  
[generic](https://cornswrold.tistory.com/180)
  
Map은 인터페이스. HashMap은 클래스. 우리는 인터페이스를 이용함으로써 다형성을 이용해 코드를 구현할 수 있습니다.  
구체클래스에 의존하지 않게 되어 나중에 코드의 변경사항이 생긴다하더라도 일일이 doc을 쓰는 로직들을 수정할 필요가 없습니다.  
  (그저 Map을 구현한 구체 클래스의 생성만 바꿔주면 된다. HashMap 대신 LinkedHashMap 이라던지...)

## <> 는 무엇인가, 왜 쓰는지?
`Diamond Operator` 라고 합니다.  
제네릭타입의 타입 추론을 컴파일러가 대신해줍니다.  
**이제 저는 매번 제네릭 자료형을 명시할때마다 반복적으로 왼쪽 오른쪽에 자료형을 적을 필요가 없게 됩니다.**  
개발자의 코드 생산성을 위한 자바7의 신기능입니다.  
```java
// jdk 7 이전 : 선언시에도 제네릭에 타입을 명시해야함.
List<Integer> ids = new ArrayList<Integer>();

Map<String, List<String>> lessons = new HashMap<String, List<string>>();
  
// jdk 7 이후(타입추론) : 다이아몬드 연산자 사용으로 컴파일러가 알아서 추론한다. 
List<Intger> ids = new ArrayList<>();

Map<String, List<String>> lessons = new HashMap<>();
```

## private static final 의 의미?
- private : 접근 제어자. 클래스 내에서만 접근 가능함을 의미합니다. private class 는 inner class 로만 가능합니다.
- static : 클래스로더에 의해 메모리 영역에 정적 데이터를 할당합니다. 프로그램 종료 시까지 소멸되지 않습니다.
- final : 불변의 class 를 만듭니다. 상속불가능으로 만듭니다.(대표적으로 String class) final 변수는 초기화 시 값이 더이상 변경되지 않습니다. 값의 불변성을 만듭니다.

## Exception 에 대해 설명해봐라
모든 Exception은 Throwable을 상속합니다.  Error와 Exception으로 나뉘고 Exception은 우리 우리가 처리해야할 클래스고 Error는 시스템상 오류입니다.  
Exception은 **checked**, **Unchecked로** 나뉩니다.checked는 우리가 빌드 전에 처리해야만 합니다.안 그럼 컴파일러가 거부를 합니다.  
보통 IOException이나 SQLException이 있습니다.  
Unchecked는 런타임에 발생하는 예외입니다. NPE가 대표적입니다.  보통 try-catch-finally 문으로 예외를 처리해줍니다.  

## inheritance vs composition

둘 다 클래스정의의 방법론이다. 
상속은 is-a // 포함은 has-a 관계를 표현한다.  
상속의 단점은 `상위클래스의 동작에 따라 하위 클래스의 동작이 코드 수정 없이 바뀔 수 있다.`  
effective java item 18 번에 나와있다.  
하위 클래스에서 상위 클래스 메서드를 재정의하면 상위클래스의 캡슐화를 깨뜨리게 된다. 상위 클래스 메서드의 내부 동작을 알지 못하면
예기치 못한 오류가 발생할 수 있기 때문이다.  
그래서 우리는 composition 을 활용해야 한다. composition 은 새로 만들 클래스의 내부 private 변수에 해당 클래스 인스턴스를 할당하면 된다.  
이 클래스의 핵심은 상위 클래스에 새로운 기능을 덧씌워 새로운 클래스를 만드는 것이다. 이런걸 wrapper 클래스라고 한다.  
자바는 다중상속을 하지 못하지만 이 패턴을 통해 다양한 구현체를 주입함으로써, 한 번의 클래스 작성으로 어떤 동일한 인터페이스 구현체도 활용할 수가 있다. 

- 코드 재사용
- 런타임 시에 구체 클래스 주입 가능
- 컴포지션으로 다중 상속 구현 가능
- 구현체 교체 쉬움  
