클린 코드와 그 첫걸음 네이밍

## [목차]

- 나쁜코드
- 클린코드
- 의미있는 이름짓기
- Google Java Naming Guide

## **나쁜코드**?

- 성능이 나쁜 코드  : 불필요한 연산이 들어가서 개선의 여지가 있는 코드
- 의미가 모호한 코드 : 이해하기 어렵고, 네이밍과 내용이 다른 코드
- 중복된 코드 : 비슷한 내용인데 중복되는 코드들
    
    

왜 나쁜데?

- 깨진 유리창 법칙 : 나쁜 코드는 깨진 유리창처럼 계속 나쁜 코드가 만들어지게 한다.
- 생산성 저하 : 나쁜 코드는 팀 생산성을 저하시킴, 기술 부채를 만들어 수정을 더 어렵게 함
- 새로운 시스템을 만들어야함: 현 시스템을 유지보수해 대체할 새로운 시스템 개발은 현실적으로 어렵다.

왜 나쁜 코드가 나오나?

- 일정 안에 새로운 기능을 완성해야한다.
    
    → 나쁜 코드는 생산성을 저하해 오히려 일정을 못맞춘다.
    
- 영향 범위가 넓어서
    
    → 생각보다 영향 범위가 넓어서 건드렸다가 이상한 곳에서 문제가 생김
    

## **클린 코드**?

- 바야네 스트룸스트룸
    - 깨끗한 코드는 한가지를 제대로 한다.
- 그래디 부치
    - 깨끗한 코드는 잘 쓴 문장처럼 읽힌다.
    

[정리]

- 성능이 좋은 코드
- 의미가 명확한 코드 = 가독성이 좋은 코드
- 중복이 제거된 코드

클린코드를 만들려면?

- 보이스카우트 규칙 : 시간이 지나도 언제나 깨끗하게 유지해야한다!
- 프리퀄과 원칙 : 객체 지향 설계의 원칙에 맞춰서!

---

## **의미 있는 이름 짓기**

```java
class SalesItem {
	Item Code code;
	String name;
	int count;
}

SalesItem seletedItem = salesItemRepository.getItemByCode(purchaseRequest.getItemCode())
// salesItem의 아이템을 코드로 가져와라, 구매요청한 아이템 코드로

System.out.printf(selectedITem.getName(), selectedTiem.getCount());
// seletedItem 의 이름과 수량을 가져와라.
```

**루프 속 i j k 사용하지 않는다.**

```java
for(int i=0; i<messages.size(); i++) // X
```

```java
messages.stream().forEach(          // lamda를 사용하면 의미를 명확하게 표현 가능하다.
	message
)
```

굳이 인덱스 값이 필요하지 않다면, 람다를 사용해 명확하게 표현 가능한다.

i,j,k 대신 맥락에 맞는 이름이 있다.

→ i,j → row,col / width, height

→i,j,k → row,col,depth

**통일성 있는 단어 사용하기**

- 팀에서 같이 네이밍에 대한 정해서 가는게 중요하다
    - Member/Customer/User
    - Service / Manager
    - Repository/Dao

**변수명에 타입을 넣지 않는다**

```java
String nameString -> name
Int ItemPriceAmount -> itemPrice

Account[] accountArray -> accounts

//List와 Map같은 경우는 많이 사용한다.
List<Account> accountList -> account,accountList
Map<Account> accountMap

public interface IShapeFactory -> ShapeFactory
public class ShapeFactoryImpl -> CircleFactory -> 현업에서는 많이 붙이긴 한다.
```

## **Google Java Naming Guide**

[https://google.github.io/styleguide/javaguide.html](https://google.github.io/styleguide/javaguide.html)

- package Naming Guide - 모두 소문자로 쓰고, 언더스코어를 쓰지 말아라

```java
com.example.deepspace 
```

- Class Naming Guide - 대문자로 시작

```java
//클래스는 명사, 명사구
Character, ImmutableList

//인터페이스는 명사, 명사구, (형용사)
List, Readable
ex) ClassImplelimentReable

//테스트 클래스는 Test로 끝나기
HashTest, HashIntegrationTest
```

- Method Naming Guide - 소문자로 시작

```java
//메서드는 동사, 동사구
sendMessage, stop

//jUnit 테스트에서 underscore로 사용되기도 한다
<methodUnderTest>_<state> 페턴

```
