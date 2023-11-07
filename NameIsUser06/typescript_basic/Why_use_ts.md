## 타입스크립트를 사용하는 이유

> Javascript vs Typescript

Javascript는 동적언어로 런타임에 타입이 결정되는데 만약 코드에 에러가 있다면 사용자에게 그대로 전달된다.

Typescript는 정적언어로 컴파일 단계에 타입이 결정되므로 개발하면서 에러가 발생하기 때문에 안정적으로 코드를 작성할 수 있다.

> Javascript 예시

```js
function add(num1, num2) {
  return num1 + num2;
}

add();
add(1);
add(1, 2);
add(1, 2, 3);
add("Hello", "world");
```

위와같은 자바스크립트 코드는 에러가 없지만 원하는 순기능을 하지 않을 수 있다는 문제점과 잘못된 사용을 정확히 감지하지 못하고 개발할 수 있다.

> Typescript 예시

```ts
function add(num1: number, num2: number) {
  return num1 + num2;
}

add(1, 2);
add(1, 2, 3); // error
add("Hello", "world"); // error
```

위와같은 타입스크립트 코드는 어떤 기능을 하는 함수인지 명확하게 보여주고 잘못된 사용에 따라 에러를 발생시켜 개발에 도움이 된다.
