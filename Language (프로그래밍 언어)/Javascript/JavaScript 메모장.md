# JavaScript 메모장

---

### This

- **함수의 실행 컨텍스트를 가리키는 예약어** (함수가 실행되는 환경)
- 상황에 따라 다른 값을 가짐.
- 종류
  1. **전역 공간에서의 this = window 또는 global, 가장 기본적인 컨텍스트, 글로벌(전역) 컨텍스트**
  2. **객체의 속성함수 내에서의 this = 해당 객체를 가르킴.**
  3. **일반 함수(함수 선언문) 내에서의 this = 지정되지 않음. 따라서 자동적으로 window를 바라보게 됨**
  4. **생성자 함수 내에서의 this = 생성될 인스턴스를 가르킴**
  5. **비동기 처리에서의 화살표 함수가 아닌 일반 함수 내에서의 this = undefined**

---

**화살표 함수**

- 주의할 점

  1. 무조건 익명함수로만 사용할 수 있음

  2. 객체의 속성함수 또는 생성자 함수를 작성할 때는 사용하지 않는다.

  3. addEventListener()의 콜백함수를 작성할 때에도 의도적인 경우가 아니라면 사용하지 않는게 좋다. 함수 선언문으로 작성해야 해당 이벤트 리스너가 호출된 엘리먼트가 this에 올바르게 바인딩된다. 화살표 함수로 작성하면 this가 window로 바인딩된다.

- **this 바인딩**

  - function으로 선언한 함수를 실행할 땐 this가 존재하긴 하지만 지정하지 않는데, **화살표 함수에는 this가 아예 없다.**
  - **JavaScript에서는 어떤 식별자(변수)를 찾을 때 현재 환경에서 그 변수가 없으면 바로 상위 환경을 검색한다.** 그렇게 점점 상위 환경으로 타고 타고 올라가다가 변수를 찾거나 가장 상위 환경에 도달하면 그만둔다. **화살표 함수에는 this라는 변수 자체가 존재하지 않기 때문에 그 상위 환경에서의 this를 참조하게 된다.**

---

### 배열 메소드 정리

- 가변 (Mutable)

  > ✅ push(element)\*\*: 배열의 끝에 하나 이상의 요소 추가
  >
  > ✅ pop()\*\*: 배열의 마지막 요소 삭제
  >
  > ✅ **unshift(element)**: 배열의 맨 앞에 하나 이상의 요소 추가
  >
  > ✅ **shift()**: 배열의 맨 앞 요소 삭제
  >
  > ✅ **splice(startIndex, deleteCount, element)**: 배열의 기존 요소를 삭제 또는

- 불변 (Immutable)

  > ✅ concat(array 또는 element)\*\*: 인자로 주어진 배열이나 요소들을 기존 배열에 합침
  >
  > ✅ slice(startIndex, endIndex)\*\*: startIndex 부터 endIndex-1까지에 대한 얕은 복사본을 반환
  >
  > ✅ join(separator)\*\*: 배열의 모든 요소를 연결해 하나의 문자열로 반환
  >
  > ✅ map(callback)\*\*: 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환한다.
  >
  > ✅ filter(separator)\*\*: 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환한다.

---

### 객체 변경 없이 데이터 수정하기 예제

```javascript
var player = { score: 1, name: "Jeff" };

var newPlayer = Object.assign({}, player, { score: 2 });
// 이제 player는 변하지 않았지만 newPlayer는 {score: 2, name: 'Jeff'}입니다.

// 객체 spread 구문을 사용한다면 이렇게 쓸 수 있습니다.
// var newPlayer = {...player, score: 2};
```

---
