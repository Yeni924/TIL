# [Error - JS] Cannot read properties of undifined

**[문제]**

```jsx
var fileExtension = IMG_FILE[0].name.split('.').pop().toLowerCase();
```

- 업로드 한 이미지 파일의 형식을 알기 위해 위와 같이 선언했을 때, 객체 참조 오류가 발생했다.
- 이미지 파일을 업로드 하지 않았을 때 IMG_FILE의 객체가 선언되지 않아서 발생한 문제였다.

**[원인]**

- 스크립트 코드에서 다른 객체에 접근할 때 해당 객체가 정의 되지 않았을 때 **Cannot read properties of undefined** 오류가 발생 한다.
- 해당 오류를 방지하려면 **Optional Chainig** 연산자를 활용할 수 있다.

**[해결]**

1) 방법 1

```jsx
if (typeof IMG_FILE !== 'undefined' && IMG_FILE.length > 0) {
    var fileExtension = IMG_FILE[0].name.split('.').pop().toLowerCase();
    // 나머지 작업 수행
} else {
    console.log('IMG_FILE 배열이 정의되지 않았거나 비어 있습니다.');
}
```

- typeof로 객체 타입이 정의 되었는지 와, IMG_FILE 배열의 길이가 0 보다 큰지 확인하는 방식으로, 변수의 존재 여부와 배열이 비어있는지 확인 후, 존재할 때 업로드 한 이미지 파일 형식을 가져오게 한다.

2) 방법 2

```jsx
var fileExtension = IMG_FILE[0]?.name.split('.').pop()?.toLowerCase();
```

- Optional Chaning 연산자를 활용 해서, IMG_FILE 배열의 첫 번째 요소가 정의 되어있으면 `name` 속성에 접근하고, 정의가 되어 있지 않으면 `undefined` 를 반환한다.
