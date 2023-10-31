# function

## 기본 형태

## 옵셔널 파라미터

```typescript
function hello(name?: string): string {
  return `Hello, ${name || "world"}`;
}

function hello(name = "world"): string {
  return `Hello, ${name}`;
}

function hello(name: string | undefined, name: string): string {
  if (age !== undefined) {
    return `Hello, ${name}. You are ${age}.`;
  } else {
    return `Hello, ${name}`;
  }
}

const result1 = hello();
const result2 = hello("John");
const result3 = hello(undefined, "John");
```

- ? 를 사용해서 옵셔널 파라미터를 사용할 수 있다.
- 옵셔널 파라미터 대신 기본값을 적용시킬 수 있다.
  - 기본값을 넣어주면 옵셔널 파라미터는 자동으로 적용된다.
- 옵셔널 파라미터 뒤에 다른 파라미터가 올 수 없다.
  - 굳이 사용하고 싶다면 타입이 undefined도 올 수 있게 한 뒤, 파라미터에 undefined를 명시해줘야 한다.

## 전개 연산자

```typescript
function add(...nums: number[]) {
  return nums.reduce((result, num) => result + num, 0);
}

add(1, 2, 3);
add(1, 2, 3, 4, 5);
```

- 전개 연산자를 사용하면 전달받은 매개변수를 배열로 사용할 수 있다.

## this

```typescript
interface User {
  name: string;
}

const Sam: User = { name: "Sam" };

function showName(this: User, age: number, gender: "m" | "f") {
  console.log(this.name, age, gender);
}

const a = showName.bind(Sam);
a(30, "m");
```

- 함수 안에서 this를 사용하고 싶을 때 매개변수의 개수에 상관없이 맨 앞에 this의 자료형을 명시해준다.

## 오버로드

```typescript
interface User {
  name: string;
  age: number;
}

function join(name: string, age: number): User;
function join(name: string, age: string): string;
function join(name: string, age: number | string): User | string {
  if (typeof age === "number") {
    return {
      name,
      age,
    };
  } else {
    return "나이는 숫자로 입력해주세요.";
  }
}

const sam: User = join("sam", 30);
const jane: string = join("sam", "30");
```

- 매개변수의 타입과 개수에 따라 유동적으로 오버로드를 사용할 수 있다.
