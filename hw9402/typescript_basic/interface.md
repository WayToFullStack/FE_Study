# interface

## interface의 개념

- 상호 간에 정의한 약속 혹은 규칙을 의미
- 타입스크립트는 아래의 내용으로 정의할 수 있음
  - 객체의 스펙
  - 함수의 파라미터
  - 함수의 스펙
  - 배여로가 객체를 접근하는 방식
  - 클래스

## 사용하는 이유

```typescript
const user = {
  name: "name",
  age: 18,
};

console.log(user.age);
```

위 코드를 실행했을 때 user.age 부분에서 에러가 발생한다. 출력하려는 오브젝트의 속성의 정보가 없기 때문이다.

그래서 이를 해결하기 위해 interface를 사용한다.

또한 interface에 없는 다른 속성은 넣을 수 없기 때문에 유지보수에 용이하고, 자동완성이 더 수월해진다.

## 사용법 (기본 타입)

```typescript
type Score = 'A' | 'B' | 'C' | 'F';

interface User {
  name: string;
  age: number;
  gender?: string;
  readonly birth: number;
  [grade: number]: Score;
};

const user: User {
  name: 'name',
  age: 18,
  1: 'A',
};

console.log(user.age);
```

- 오브젝트 형태로 선언해 속성이름과 그에 대한 타입을 정해주면 된다.
- 옵셔널하게 정하고 싶다면 속성이름 뒤에 '?'를 붙여준다.
- 처음 값을 정해주고 변경이 되지 않게 하고 싶다면 속성 이름 앞에 readonly를 작성한다.
- 만약 객체가 갖는 값은 다르지만 타입은 동일한 속성을 여러개 지닐 수 있게 하고 싶다면 인덱스 서명을 사용한다.
  - 예시 코드에 있는 grade 자리엔 아무거나 들어거도 상관이 없다. 명시적으로 작성하는 것일 뿐이다.
- 들어가는 값을 강제하고 싶다면 type 자료형을 사용할 수 있다. 위 예시코드의 Score처럼 '|'를 구분자로 사용해서 들어갈 값을 적어주면 된다.

## 사용법 (함수)

```typescript
interface Add {
  (num1: number, num2: number): number;
}

const add: Add = (x, y) => {
  return x + y;
};
```

## 사용법 (클래스)

```typescript
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

const b = new Bmw("red");
```

- class에서 interface를 타입으로 정해줄 때 implements 키워드를 사용한다.
- interface끼리 extends 키워드를 사용해서 상속할 수 있다.
  - 여러 interface들을 한 번에 상속받을 수 있다.
