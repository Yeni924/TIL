# [C#/ JSON] JSON 데이터 다루기 JSON 파싱

**※ C#  JSON 변환하는 방법 간략 정리**

JSON(JavaScript Object Notation)은 데이터를 쉽게 교환하기 위해 사용되는 양식으로, 속성-값이 쌍 { Name="KWON", Age = 10 } 된 형태다.

객체 데이터를 통신하기 위해서 객체→ JSON, JSON → 객체로 변환하는 과정을 거치게 된다.

 1. 객체 → JSON 변환 / 직렬화(**Serialization**)

1. JSON → 객체로 변환 / 역직렬화(**Deserialization**)

**[환경 구성]**

- Newtonsoft.Json 패키지 설치
    - 도구 > NuGet 패키지 관리자 > 솔루션용 NuGet패키지 관리
![image](https://github.com/Yeni924/TIL/assets/80144039/a621ce54-6bcc-49c7-9841-c8e3c8c16193)


- 설치 완료 시, Newtonsoft.Json이 추가 된 것을 확인할 수 있다.
![image](https://github.com/Yeni924/TIL/assets/80144039/86f25c02-a512-4712-be50-ad9f75d7b704)



**[예제]**

1. 직렬화
2. 역직렬화
3. 배열 객체 직렬화
4. 배열 객체 역직렬화

```csharp
using Newtonsoft.Json;
using System;
using System.Collections.Generic;

namespace Project3
{
    public class JsonTest
    {
        public string Name { get; set; }
        public int Age { get; set; }
       
    }

    class Class1
    {
        public static void Main(string[] args)
        {
            //1. 직렬화 하기
            var testData = new JsonTest { Name="KWON", Age = 10};
            var jsonSerialize = JsonConvert.SerializeObject(testData);

            Console.WriteLine(jsonSerialize);
            Console.WriteLine("------------------------------------------------------------------------");

            //2. 역직렬화 하기
            var jsonDeserialize = JsonConvert.DeserializeObject<JsonTest>(jsonSerialize);
            Console.WriteLine($"{jsonDeserialize.Name}, {jsonDeserialize.Age}");
            Console.WriteLine("------------------------------------------------------------------------");

            //3. 배열 객체 직렬화하기
            var testList = new List<JsonTest>();
            testList.Add(new JsonTest { Name = "KIM", Age = 20 });
            testList.Add(new JsonTest { Name = "LEE", Age = 25 });

            var jsonSerializeList = JsonConvert.SerializeObject(testList);
            Console.WriteLine(jsonSerializeList);
            Console.WriteLine("------------------------------------------------------------------------");

            //4. 배열 객체 역직렬화
            var jsonDeserializeList = JsonConvert.DeserializeObject<List<JsonTest>>(jsonSerializeList);

            foreach (var json in jsonDeserializeList)
            {
                Console.WriteLine($"{json.Name}, {json.Age}");
            }

        }
    }

}

```

**[결과]**
![image](https://github.com/Yeni924/TIL/assets/80144039/54818009-5be6-4d6b-88b0-fcfddf4c025e)
