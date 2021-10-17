## union type - 유니온타입(or)

유니온 타입(Union Type)이란 자바스크립트의 OR 연산자(||)와 같이 A이거나 B이다 라는 의미의 타입
하나의 타입이상 쓸수 있게 하는 것이 유니온 타입, or 느낌

```ts
function logMessage(value: string | number) {
    if (typeof value === "number") {
        value.toLocaleString();
    }
    if (typeof value === "string") {
        value.toLocaleString();
    }
    throw new TypeError('value musg be string or number')
}
logMessage("hello");
logMessage(1090);
```

유니온타입은 두개의 인터페이스에서 겹치는 것만 쓸 수 있다.
```ts
interface Developer {
    name: string;
    skill: string;
}

interface Person {
    name: string;
    age: number;
}

//여기서는 보장된 속성에서 접근가능하다.
 function askSomeone(someone: Developer | Person) {
     // 가능 
     someone.name;
     // 불가능
     someone.skill;
     someone.age;
 }
```


## intersection type - 인터셉션 타입 (and)
인터섹션 타입(Intersection Type)은 여러 타입을 모두 만족하는 하나의 타입을 의미

```ts
//인터셉션 타입 and 연산자
let cap: string & number & boolean;
//모든 속성의 타입을 보장한다.
function askSomeone(someone: Developer & Person) {
    someone.name;
    someone.skill;
    someone.age;
}
```
