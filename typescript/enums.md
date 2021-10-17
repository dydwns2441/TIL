## enums

이넘은 특정 값들의 집합을 의미하는 자료형입니다.
예를 들면 아래와 같은 목록이 이넘이 될 수 있습니다.

```ts
enum shoes {
  Nike, //이넘은 별도의 설정을 안해주면 자동으로 0이 들어간다.
  Adidas, // 1
  sth,    // 2
}

enum shoes {
    Nike = "나이키",
    Adidas ="아디아스"
};


let myShoes = shoes.Nike // '나이키'

enum Answer {
    yes = 'Y',
    no = 'N'
}

function askQuestion(answer: string) {
    if (answer === Answer.yes) {
        console.log('정답')
    }
    if (answer === Answer.no) {
        console.log('오답')
    }
}
//이넘의 값만 들어갈수있다.
askQuestion('예스');     //안된
```
