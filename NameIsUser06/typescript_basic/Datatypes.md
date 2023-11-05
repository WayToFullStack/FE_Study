## 타입스크립트 자료형

### 선언

```ts
let a: string = "bmw";
a = 12; // error
```

타입스크립트에서 문자열 자료형의 기초적인 선언 방법이며 다른 타입으로 대입을 시도할때는 에러를 발생시킨다

```ts
let a = "bmw"; // string
a = 12; // error
```

위와같이 작성해도 자동으로 문자열로 타입이 지정된다

---

### 자료형

- string
- number
- boolean
- void
- never

```ts
let age: number = 18;
let isAdult: boolean = false;
let name: string = "name";

function sayHello(): void {
  console.log("Hello");
}

function showError(): never {
  throw new error();
}

function infLoop(): never {
  while (true) {
    // code
  }
}
```

---

### 배열

- datatype[]
- Array\<datatype>

```ts
let age1: number[] = [1, 2, 3];
let age2: Array<number> = [1, 2, 3];
```

---

### 튜플

- [typename, typename]

```ts
let b: [string, number];
b = ["z", 1];
```

---

### 열거형

```ts
enum Os {
  Window = 3,
  Ios = 10,
  Android,
}

console.log(Os["Ios"]); // 10
```

---

### null, undefined

- null: 빈 값을 할당한 상태
- undefined: 변수를 정의만 해둔 상태 (자료형이 없음)
