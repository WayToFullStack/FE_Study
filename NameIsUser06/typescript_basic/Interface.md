## 인터페이스

### 객체

```ts
type Score = "A" | "B" | "C" | "D";

interface User {
  name: string;
  age: number;
  gender?: string;
  readonly birth: number;
  [grade: number]: Score;
}

let user: User = {
  name: "xx",
  age: 30,
  birth: 2000,
  1: "A",
};

user.gender = 10;
console.log(user.name);
```

- 오브젝트 형태로 선언해 속성이름과 타입을 지정해준다.
- Optional 형으로 선언하고 싶다면 속성이름 뒤에 ?를 붙여준다.
- 변수를 선언할때만 정의하게 하고싶을때는 readonly를 앞에 붙여준다.
- grade와 같이 인덱스 서명을 사용하면 grade라는 이름 대신에 숫자를 속성이름으로 사용해도 된다.
  - grade는 인터페이스 정의를 위한 명시적인 부분이다.
- 문자열 리터럴 타입을 Score와 같이 type으로 선언하면 들어가는 값을 강제할 수 있다.

### 함수

```ts
interface Add {
  (num1: number, num2: number): number;
}

const add = function (x, y) {
  return x + y;
};

const add2: Add = (x, y) => {
  return x + y;
};

add(10, 20);
```

### 클래스

```ts
interface Car {
  color: string;
  wheels: number;
  start(): void;
}

interface Benz extends Car {
  door: number;
  stop(): void;
}

class Bmw implements Car {
  wheels = 4;

  constructor(c: string) {
    this.color = c;
  }

  start() {
    console.log("go");
  }
}

const a = new Bmw("black");
```

- class의 타입을 지정할때는 implements를 사용한다.
- interface 끼리 extends를 통해서 상속할 수 있다.
  - 다중상속이 가능하다.
