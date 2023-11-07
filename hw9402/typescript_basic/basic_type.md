## 기본 타입

- string
- boolean
- number

## 배열

- type[]
- Array\<type\>

## 튜플

- [type, type, type...]
- 정해진 타입과 위치에 맞게 사용해야 한다.
- ```typescript
  let 튜플: [string, number] = ["a", 1]; // O
  let 튜플: [string, number] = [1, "a"]; // X
  ```

## void, never

- void: 함수에서 아무 것도 반환하지 않을 때 사용
- never: 에러만 던져주거나, 절대 끝나지 않는 함수에 명시

## enum

- 비슷한 값들끼리 묶어주는 역할
- ```typescript
  enum Os {
    Windows = "windows",
    MacOS = "macos",
    Android = "android",
    IOS = "ios",
  }
  let myOs: Os;
  myOs = Os.MacOS;
  ```
- 만약 값을 매겨주지 않으면 인덱스 번호로 매겨진다. (순서대로 0, 1, 2, ...)
- 타입으로 지정해두면 enum에 있는 값만 들어갈 수 있다.

## null, undefined

- null: 빈 값을 할당한 상태
- undefined: 변수를 선언하고 값을 할당하지 않은 상태. 즉, 자료형이 없는 상태

## 타입 지정 하는 법

- 변수명 뒤에 콜론을 구분자로 타입을 지정해주면 된다.
- ```typescript
  let 문자열: string = "문자열";
  ```
