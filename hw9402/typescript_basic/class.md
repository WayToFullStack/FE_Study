# class

```typescript
class Car {
  (public / protected / private) color: string;

  constructor(color: string) {
    this.color = color;
  }

  start() {
    console.log("start");
  }
}

const bmw = new Car("red");
```

## public

- 자식 클래스, 클래스 인스턴스 등 모두 접근 가능한 접근 제어자

## protected

- 자식 클래스에서만 접근 가능한 접근 제어자

## private

- 해당 클래스 내부에서만 접근 가능한 접근 제어자

# abstract class

```typescript
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

const bmw = new Car("red"); // X

class Bmw extends Car {
  constructor(color: string) {
    super(color);
  }

  doSomething() {
    console.log("doSomething");
  }
}
```

- new 키워드를 통한 객체 생성이 불가능하다
- super() 키워드로만 객체를 생성할 수 있다.
- abstract 키워드가 붙은 메서드는 자식 메서드에서 구체적인 구현을 해줘야 한다.
