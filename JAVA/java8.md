## JAVA8 의 주요한 추가 기능들 아는 것들을 설명해달라
- Stream API 추가
- LocalDateTime, LocalDate 추가 
- lambda 표현식의 등장

## Stream 을 써보셨나요? 간단하게 설명해주세요
- 자바에서 추상화된 데이터 파이프라인을 제공해주는 인터페이스
- 중간연산과 최종연산으로 메서드가 나뉘게 됨.
- 최종연산이 호출되지 않으면 그 이전까지의 연산메서드들은 레이지 로딩이 됨
- 원본에 영향을 끼치지 않고 한번 쓰인 스트림은 재활용될 수 없음
- 코드가 간결화되고 동작들을 눈으로 읽기가 쉬워짐
## lambda 표현식은 Object인가요? (instance of Object 가 true)

네. 모든 람다 표현식은 자바 오브젝트입니다. functionalInterfacie의 구현체입니다. 
