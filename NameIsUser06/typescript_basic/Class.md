## class

### public

- 모두 접근 가능한 접근 제어자

### protected

- 자식 클래스에서만 접근 가능한 접근 제어자

### private

- 해당 클래스 내부에서만 접근 가능한 접근 제어자

```ts
class Car {
  (public / protected / private) color: string;

  constructor(color: string) {
    this.color = color;
  }

  start() {
    console.log("start");
  }
}

const bmw = new Car("black");
```

## abstract class

```ts
class Car {
  (public / protected / private) color: string;

  constructor(color: string) {
    this.color = color;
  }

  start() {
    console.log("start");
  }

  abstract class doSomething(): void;
}

const bmw = new Car("black"); // X

class Bmw extends Car {
  constructor(color: string) {
    super(color);
  }

  doSomething() {
    console.log("doSomething");
  }
}
```

- new 키워드를 통한 객체 생성이 불가능하고 super()를 통해서만 객체를 생성할 수 있다.
- abstract 키워드가 붙은 메서드는 상속받은 자식 메서드에서 구체적인 구현을 해주어야 한다.
