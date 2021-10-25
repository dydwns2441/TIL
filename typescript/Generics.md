# Generics

## 정의

- 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미
- 재사용성이 높은 컴포넌트를 만들 때 자주 활용되는 특징,
- 특히, 한가지 타입보다 여러 가지 타입에서 동작하는 컴포넌트를 생성하는데 사용

## 예시

### 기본
```ts
function getText(text) {
  return text;
}

getText('hi'); // 'hi'
getText(10); // 10
getText(true); // true
```

### 제네릭이 적용된 함수
```ts
function getText<T>(text: T): T {
  return text;
}

getText<string>('hi');
getText<number>(10);
getText<boolean>(true);

// function getText<string>(text: string): string {
//  return text;
// }
```

## 제네릭을 사용하는 이유

- any를 쓰면 되는거 아닌가 하는 의문
- 이렇게 한다고 해서 함수의 동작에 문제가 생기지 않는다.
- 하지만 함수의 인자로 어떤 타입이 들어갔고, 어떤 값이 반환되는지는 알 수가 없다.
- any는 타입 검사를 하지 않음
- 이문제를 해결하는게 제네릭

```ts
function logText(text: any): any {
  return text;
}

function logText<T>(text: T): T {
  return text;
}

// #1 이렇게 써야 할 것을 2번처럼 쓸 수 있게 된다
const text = logText<string>("Hello Generic");
// #2
const text = logText("Hello Generic");
```

## 제네릭 제약조건

- 제네릭 함수에 어느정도 타입 힌트를 줄 수 있는 방법이 있다

```ts
// length속성이 있는 함수만 받고 싶다 number를 받아 올 경우 에러 발생
function logText<T>(text: T): T {
  console.log(text.length); // Error: T doesn't have .length
  return text;
}

// 아래처럼 바꾸게 되면 length에 대해 동작하는 인자만 넘겨 받을 수 있다
interface LengthWise {
  length: number;
}

function logText<T extends LengthWise>(text: T): T {
  console.log(text.length);
  return text;
}

logText(10); // Error, 숫자 타입에는 `length`가 존재하지 않으므로 오류 발생
logText({ length: 0, value: 'hi' }); // `text.length` 코드는 객체의 속성 접근과 같이 동작하므로 오류 없음
```

## 객체의 속성을 제약하는 방법

- 두 객체를 비교할 때도 제네릭 제약 조건을 사용할 수 있다
- 제네릭을 선언할 때 <O extends keyof T> 부분에서 첫 번째 인자로 받는 객체에 없는 속성들은 접근할 수 없게끔 제한하였다

```ts
function getProperty<T, O extends keyof T>(obj: T, key: O) {
  return obj[key];  
}
let obj = { a: 1, b: 2, c: 3 };

getProperty(obj, "a"); // okay
getProperty(obj, "z"); // error: "z"는 "a", "b", "c" 속성에 해당하지 않습니다.
```

