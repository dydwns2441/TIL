# TypeScript

## Interface와 type
인터페이스는 상호 간에 정의한 약속 혹은 규칙을 의미합니다. 타입스크립트에서의 인터페이스는 보통 다음과 같은 범주에 대해 약속을 정의할 수 있습니다.
1. 객체의 스펙(속성과 속성의 타입)
2. 함수의 파라미터 
3. 함수의 스펙(파라미터, 반환 타입 등)
4. 배열과 객체를 접근하는 방식
5. 클래스

### 기본

```ts
interface User {
    age: number,
    name: string,
}

//변수에 인터페이스 활용
let seho: User = {
    age: 33,
    name:'세호'
};

//함수에 인터페이스 활용
function getUser(user) {
    console.log(user)
}

const capt:User = {
    name: '캡틴',
    age: 1,
}
//네임 뿐만아니라 age도 같이 있어야 가능하다.

getUser(capt);
```

### 함수의 스펙에 인터페이스를 활용

```ts
//* 함수의 스펙(구조)에 인터페이스를 활용
interface Sumfunction {
    (a: number, b: number): number;
}

let sum: Sumfunction;
sum = function (a:number,b:number):number {
    return a + b;
}
```

### 인덱싱

```ts
//인덱싱
interface StringArray {
    [index:number]:string
}

let arr:stringArray = ["a", "b", "c"];
arr[0] = "ff"; //가능
// arr[0] = 9;    //불가능
```

### 인터페이스 딕셔너리 패턴, 확장(상속)

```ts
//* 딕셔너리 패턴
interface stringRegexDictionary {
    [key: string]: RegExp;
}

let obj:stringRegexDictionary = {
    // sth: /abc/,
    //? cssFile:'css'  //정규표현식이 와야하는데 문자열이 와서 오류
    jsFile: /\.js$/,
}
// obj['jsFile'] = "a"  //접근 불가능, 정규표현식이 아님
//일반 문자열을 넣어 오류가 남
Object.keys(obj).forEach((value) => { });

//인터페이스 확장
interface Person {
    name: string,
    age:number,
}

interface Developer extends Person {
    //name과 age가 필요없어진다. // 확장
    language: string,
}

let hulk: Developer = {
    name: "hulk",
    age: 200,
    language: "typescript"
}
```


## Type 별칭(Type Aliases)

타입 별칭은 특정 타입이나 인터페이스를 참조할 수 있는 타입 변수를 의미합니다. 

```ts


//타입 별칭은 특정 타입이나 인터페이스를 참조할 수 있는 타입 변수를 의미합니다.
//위와 같이 string, number와 같은 간단한 타입 뿐만 아니라
//interface 레벨의 복잡한 타입에도 별칭을 부여할 수 있습니다.
type MyString = string;
let str: MyString = 'hello';

// 타입 별칭은 새로운 타입 값을 하나 생성하는 것이 아니라
// 정의한 타입에 대해 나중에 쉽게 참고할 수 있게 이름을 부여하는 것과 같습니다.


//* 타입 별칭과 인터페이스의 가장 큰 차이점은 타입의 확장 가능 / 불가능 여부입니다. 
//* 인터페이스는 확장이 가능한데 반해 타입 별칭은 확장이 불가능합니다.
//* 따라서, 가능한한 type 보다는 interface로 선언해서 사용하는 것을 추천합니다.

//좋은 소프트웨어는 언제나 확장이 용이해야 한다는 원칙에 따라 
//가급적 확장 가능한 인터페이스로 선언하면 좋습니다 😃

// interface Person {
//     name: string;
//     age:number;
// }

type Person = {
    name: string,
    age: number
}

let seho: Person = {
    name: "seho",
    age: 100
};

//* type Todo = { id: string, title: string, done: boolean };
//* function getTodo(todo: Todo) {
    
//* }
```

### 결론
- 타입 별칭과 인터페이스의 가장 큰 차이점은 타입의 확장 가능 / 불가능 여부입니다. 
- 인터페이스는 확장이 가능한데 반해 타입 별칭은 확장이 불가능합니다.
- 따라서, 가능한한 type 보다는 interface로 선언해서 사용하는 것을 추천합니다.

출처 : 
- https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle
- 타입스크립트 입문 - 캡틴판교
