# [Java] 자바 스트림(Stream)

C# 에서 데이터를 간편하게 다루기 위해 Linq를 제공한다면, Java에서는 Stream API (함수형 프로그래밍)를 제공한다.

Stream은 데이터의 흐름으로 데이터를 처리하기 위한 연속적인 집합이고, Stream API는 데이터의 리스트, 배열 등으로 Stream(데이터 흐름)을 생성해서 데이터를 처리한다.

**Stream 특징**

- 데이터의 시퀀스로 처리 되어 한번에 하나씩 요소를 처리하지 않고 연속적으로 처리한다.
- 내부적으로 반복하는 방식으로 작동 되어 개발자가 명시적으로 반복을 제어할 필요가 없다.
- 스트림은 재사용이 불가능하다
- 중간 연산과 최종연산으로 구성된다.
    - 중간 연산 : 스트림 요소를 변환하거나 필터링
    - 최종 연산 : 스림의 요소를 소비해 결과 생성

**Stream 과정**

1. 스트림 생성 : 컬렉션, 배열 , 파일 등 데이터로부터 스트림을 생성
2. 중간 연산 
    
    
    | filter | 주어진 조건에 따라 요소를 필터링 |
    | --- | --- |
    | map | 요소를 다른 형태로 변환 |
    | flatMap | 요소를 스트림으로 매핑 |
    | distinct | 중복 요소 제거 |
    | sorted | 요소 정렬 |
    | limit | 처음 부터 몇 개의 요소만 가져오기 |
    | skip | 처음 부터 몇 개의 요소 건너뛰기 |
    | peek | 각 요소 작업  수행 후 유지 |
3. 최종 연산
    
    
    | forEach | 각 요소에 대해 주어진 동작 수행 |
    | --- | --- |
    | collect | 스트림 요소를 수집해 컬렉션 및 그룹화 형태로 반환 |
    | reduce | 스트림 요소 반복 후 하나의 값으로 줄임 |
    | count | 스트림 요소 반환 |
    | anyMatch | 주어진 조건을 만족하는 요소가 있는지 검사 |
    | allMatch | 모든 요소가 주어진 조건을 만족하는지 검사 |
    | noneMatch | 모든 요소가 주어진 조건을 만족하지 않는지 검사 |
    | findFirst | 스트림의 첫 번째 요소 반환 |
    | findAny | 스트림의 임의 요소 반환 |
    
    **[예제]**
    
    ```java
    import java.util.Arrays;
    import java.util.List;
    
    public class Test {
        public static void main(String[] args) {
            // 스트림 생성
            List<String> test = Arrays.asList("a", "bb", "c", "dd");
    
            test.stream()  // 중간 연산: 문자열 길이가 2 이상인 요소만 필터링
                  .filter(t -> t.length() >= 2)
                  .map(String::toUpperCase) // 요소를 대문자로 변환
                  .sorted() // 정렬
                  .forEach(System.out::println); // 최종 연산: 결과 출력
        }
    }
    
    ```
    
   ![image](https://github.com/Yeni924/TIL/assets/80144039/e88b0ca9-0fb7-4b37-8976-a1b332bd9769)

    **※ Stream을 사용하면?**
    
    - 스트림 API를 내부적으로 반복을 사용해서 개발자가 명시적으로 반복을 제어할 필요가 없고, 반복문과 조건문을 줄일 수 있어 코드가 간결해진다.
    
    ```java
    import java.util.Arrays;
    import java.util.List;
    
    public class Test {
        public static void main(String[] args) {
    
            String[] array = { "a", "b", "c" };
                for (int i = 0; i < array.length; i++) {
                    System.out.println(array[i]);
                }
    
            Arrays.stream(array).forEach(System.out::println); // Stream API 함수 사용
        }
    }
    
    ```
    
    **※ 자바 스트림에서 :: 는 어떻게 사용하는 걸까?**
    
    → :: 기준으로 왼쪽 객체에서 오른쪽 메소드를 사용한다는 의미다.
    
    → System.out::println로 확인하자면 System.out 객체의 pringln 메서드를 가리키는 것이고, System.out(출력 스트림 객체)에서 println (출력하는 함수)이다.
