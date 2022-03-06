# Table of contents

- [java 의 String 객체가 무엇인지 설명해봐라](#java--string---)
  - [String은 원시타입인가?](#string-)
  - [그러면 String은 스레드에서 안전한가?](#-string--)
- [String 을 비교하는 방법 '==', 's1.equals(s2)' 의 차이는?](#string-----s1equalss2--)
- [String, StringBuilder, StringBuffer 의 차이를 설명하라](#string-stringbuilder-stringbuffer---)
  - [그렇다면 메소드 안에서 선언하여 사용시에는 어떤게 권장되는가?](#------)

# java 의 String 객체가 무엇인지 설명해봐라

String은 byte(8bit) 배열을 표현하는 **불변의 객체**다.

모든 리터럴 문자열은 String 객체이다. 

`String s = "apple";`

`String s = new String("apple");`

## String은 원시타입인가?

아니다. 상태(state)와 행위(behavior)를 가지는 파생(derived type) 타입이다.

그러나 원시형처럼 new 키워드 없이 선언 가능하고, + 연산까지 가능하다.


또한 JVM 에 의해 stack이 아닌 [string pool](https://www.baeldung.com/java-string-pool) 이라는 별도 메모리 공간에서 관리된다. 

## 그러면 String은 스레드에서 안전한가?

앞서 말했듯이, 불변객체이기 때문에 당연히 안전하다.

만약 존재하는 문자열을 변조하려고 하면 새로운 문자열 객체가 생성될 뿐이고 원본에는 해가 없다.


# String 을 비교하는 방법 '==', 's1.equals(s2)' 의 차이는?

`==`는 객체의 주소 참조가 같은지, `s1.equals(s2)` 는 어휘가 같은지를 본다.

```java
String string1 = "apple";
String string2 = new String("apple");

assertThat(string1.equals(string2)).isTrue();
assertThat(string1 == string2).isFalse();
```

# String, StringBuilder, StringBuffer 의 차이를 설명하라

String 객체는 불변 객체라서 +연산으로 더 할 경우 메모리를 많이 사용한다.

문자열을 붙일때마다 새로운 객체를 생성해야 하기 때문이다.

그래서 문자열 연산이 많은 경우 StringBuilder, StringBuffer 를 사용하는게 권장된다.

StringBuilder는 Thread-safe 하지 않다. StringBuffer 는 쓰레드 환경에서 안전하다.

따라서 멀티쓰레드 환경에서는 StringBuffer 가 권장된다.


## 그렇다면 메소드 안에서 선언하여 사용시에는 어떤게 권장되는가?

1. StringBuffer
2. StringBuilder
3. 뭐를 쓰든 무관

메서드 내에서 사용한다는 건 쓰레드 간의 경합이 발생하지 않는다는 의미이므로

Thread-safe 에 대한 비용 발생이 없는 StringBuilder 가 낫다.



[https://www.baeldung.com/java-string-interview-questions](https://www.baeldung.com/java-string-interview-questions)
