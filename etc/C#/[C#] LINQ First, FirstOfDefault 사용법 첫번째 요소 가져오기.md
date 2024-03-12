# [C#] LINQ First, FirstOfDefault 사용법 첫번째 요소 가져오기

- First()
- FirstOrDefault()
- Last()
- LastOrDefault()

First(), FirstOrDefault() 함수는 요소의 첫 번째 요소를 검색하거나 가져오는데 사용 된다.

1. **First**
    - 시퀀스에 지정된 조건을 만족하는 첫 번째 요소를 검색하거나, 첫 번째 요소를 가져오는데 사용
    - 단, 조건을 만족하는 요소가 없을 때는 **예외**가 발생한다.

**[예제]**

```csharp
using System;
using System.Linq;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] testNumbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
            string[] testString = { "가", "나", "다" };

            // 첫번째 요소 찾기
            var firstNumber = testNumbers.First();
            var firstString = testString.First();

            // 조건에 만족하는 첫번째 요소 찾기
            var equalsNumber = testNumbers.First(t => t.Equals(7));
            var equalsString = testString.First(t => t.Equals("나"));

            // 조건에 만족하는 요소가 없을 때
           // var errorNumber = testNumbers.First(t => t.Equals(11));
           // var errorString = testString.First(t => t.Equals("라"));

            Console.WriteLine("firstNumber : " + firstNumber);
            Console.WriteLine("firstString : " + firstString);
            
            Console.WriteLine("equalsNumber : " + equalsNumber);
            Console.WriteLine("equalsString : " + equalsString);

            ///Console.WriteLine("errorNumber : " + errorNumber);
            ///Console.WriteLine("errorString" + errorString);
        }
    }
}

```

![image](https://github.com/Yeni924/TIL/assets/80144039/af0b109b-5f0a-4bca-8c39-467009f4fd23)

![image](https://github.com/Yeni924/TIL/assets/80144039/eaf4f7aa-83db-4043-badc-c7039d609d0c)

- 결과 확인 시,  “시퀀스에 일치하는 요소가 없습니다.” InvalidOperationException 예외가 발생한다.

1. **FirstOrDefault**
- 지정된 조건을 만족하는 첫 번째 요소를 반환한다.
- 해당하는 요소가 없을 경우에는 **기본 값**(null)을 반환한다.
    - int : 0
    - bool: false

**[예제]**

```csharp

using System;
using System.Linq;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] testNumbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
            string[] testString = { "가", "나", "다" };

                       
            // 첫번째 요소 찾기
            var firstNumber = testNumbers.FirstOrDefault();
            var firstString = testString.FirstOrDefault();

            // 조건에 만족하는 첫번째 요소 찾기
            var equalsNumber = testNumbers.FirstOrDefault(t => t.Equals(7));
            var equalsString = testString .FirstOrDefault(t => t.Equals("나"));

             // 조건에 만족하는 요소가 없을 때
            var errorNumber = testNumbers.FirstOrDefault(t => t.Equals(11));
            var errorString = testString .FirstOrDefault(t => t.Equals("라"));
        
		        Console.WriteLine("firstNumber : " + firstNumber);
		        Console.WriteLine("firstString : " + firstString);
		
		
		        Console.WriteLine("equalsNumber : " + equalsNumber);
		        Console.WriteLine("equalsString : " + equalsString);

            Console.WriteLine("errorNumber : " + errorNumber);
            Console.WriteLine("errorString" + errorString);

        }
    }
}

```

![image](https://github.com/Yeni924/TIL/assets/80144039/65947f4d-21d0-4eb3-b988-7e02d391762e)


- 같은 예제로 firstOrDefault로 변경해보면 예외를 발생하지 않고 기본 값을 반환하는 것을 확인할 수 있다.

**[결론]**

 First()의 경우 조건을 만족하는 요소가 없으면 예외를 발생 시키기 때문에 요소가 포함되는지 확실하지 않을 때는 FirstOrDefault()를 사용하는 것이 적합하다.

- 첫 번째 요소가 아닌 마지막 요소 검색은 Last()와 LastOrDefault()가 있으며 사용 방법은 First()와 FirstOrDefault()와 유사하다.
