## generic

- 데이터의 타입을 클래스 내부에서 지정하는 것이 아닌 외부에서 사용자에 의해 지정되는 것

## generic을 사용하는 이유

```typescript
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

- 데이터의 타입은 다른데 같은 함수/속성을 재사용하고 싶을 때 사용한다.

## 사용법

```typescript
function getSize<T>(arr: T[]): number {
  return arr.length;
}

const arr1 = [1, 2, 3];
getSize<number>(arr1);

const arr2 = ["a", "b", "c"];
getSize<string>(arr2);

const arr3 = [false, true, true];
getSize<boolean>(arr3);

const arr4 = [{}, {}, { name: "Tim" }];
getSize<object>(arr4);
```

```typescript
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

- \<T> 로 사용할 타입을 변수화 시킨다.
- 사용하는 곳에서 타입과 함께 선언/사용하면 된다.
- <> 안에 바로 인터페이스를 선언하지 않고 바로 작성할 수 있다.
- extends 키워드를 사용해서 없는 속성을 추가하거나 그 속성의 타입을 바꿔줄 수 있다.
