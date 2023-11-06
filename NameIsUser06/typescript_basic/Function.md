## 함수

### 옵셔널 파라미터

```ts
function hello(name?: string): string {
  return `Hello, ${name || "World"}`;
}

function hello(name = "World"): string {
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

- ?를 사용해서 옵셔널 파라미터를 사용할 수 있다.
- 기본값을 적용하여 옵셔널 파라미터로 사용할 수 있다.
- 옵셔널 파라미터 뒤에는 다른 파라미터가 올 수 없다.
  - 옵셔널이 아닌 파라미터부터 작성해야한다.
  - 꼭 옵셔널 파라미터 먼저 사용하고 싶다면 | 를 사용해서 undefined를 명시해주어야 한다.

### 전개연산자

```ts
function add(...nums: number[]) {
  return nums.reduce((result, num) => result + num, 0);
}

add(1, 2, 3);
add(1, 2, 3, 4, 5);
```

- 전개연산자를 사용하면 전달받은 매개변수의 개수와 상관없이 배열로 사용할 수 있다.

### this

```ts
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

- 함수 안에서 this를 사용하고 싶을 때는 매개변수의 개수와 상관없이 맨 앞에 this로 사용할 자료형을 명시해준다.

### 오버로딩

```ts
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

- 매개변수의 타입과 개수에 따라 오버로딩을 사용할 수 있다.
