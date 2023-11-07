## Literal

```ts
const userName1 = "Bob";
let userName2: string | number = "Tom";
```

- const는 변하지 않는 상수를 정의할 때 사용한다.
- let은 변할 수 있는 변수를 정의할 때 사용한다.

## Union

```ts
interface Car {
  name: "car";
  color: string;
  start(): void;
}

interface Mobile {
  name: "mobile";
  color: string;
  call(): void;
}

function getGift(gift: Car | Mobile) {
  console.log(gift.color);
  if (gift.name === "car") {
    gift.start();
  } else {
    gift.call();
  }
}
```

- 여러 타입을 가질 수 있게 지정하는 것이 Union 타입이다.
- 둘의 타입이 공통으로 가지지 않는 속성에 접근하면 에러가 발생하기 때문에 타입을 먼저 체크 해주어야 한다.

## Intersection

```ts
interface Car {
  name: string;
  start(): void;
}

interface Toy {
  name: string;
  color: string;
  price: number;
}

const toyCar: Toy & Car = {
  name: "타요",
  start(): {},
  color: "blue",
  price: 1000,
};
```

- 여러 개의 타입을 합쳐서 사용할 때 Intersection을 사용한다.
