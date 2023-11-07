## generic

- 데이터 타입의 지정을 클래스 내부에서 결정하는 것이 아닌 사용자에 의해 결정되는 것

### generic을 사용하는 이유

```ts
function getSize(arr: number[] | string[] | boolean[] | object[]): number {
  return arr.length;
}

const arr1 = [1, 2, 3];
getSize(arr1);

const arr2 = ["a", "b", "c"];
getSize(arr2);

const arr3 = [false, true, true];
getSize(arr3);

const arr4 = [{}, {}, { name: "Tim" }];
getSize(arr4);
```

- 같은 내용의 함수를 다양한 자료형에 대한 처리를 하고싶을 때 사용한다.

### 사용법

```ts
function getSize<T>(arr: T[]): number {
  return arr.length;
}

const arr1 = [1, 2, 3];
getSize<number>(arr1);

const arr2 = ["a", "b", "c"];
getSize<string>(arr2);

const arr3 = [false, true, true];
getSize<boolean>(arr3);

const arr4 = [{}, {}, { name: "Tom" }];
getSize<object>(arr4);
```

```ts
interface Moblie<T> {
  name: string;
  price: number;
  option: T;
}

const m1: Mobile<object> = {
  name: "s21",
  price: 1000,
  option: {
    color: "red",
    coupon: false,
  },
};

const m2: Mobile<{
  color: string;
  coupon: boolean;
}> = {
  name: "s21",
  price: 1000,
  option: {
    color: "red",
    coupon: false,
  },
};

const m3: Mobile<string> = {
  name: "s20",
  price: 1000,
  option: "good",
};

function showName<T extends { name: string }(data: T)>: string {
  return data.name;
}
```

- \<T> 를 사용해 타입을 변수화 시킨다.
- <> 안에 바로 사용할 수 있다 (정의가 필요 없다).
- 사용하는 곳에서 타입과 함께 선언 후 사용하면 된다.
- extends를 특정 속성의 타입을 바꿔주거나 새로운 속성을 추가할 수 있다.
