# React 메모장

---

### 불변성이 중요한 이유 

- 리엑트 공식 문서 중에서...

> ✅ 복잡한 특징들을 단순하게 만듦.
>
> - 특정 행동을 취소하고 다시 실행하는 기능 구현이 쉬움
> - 이력을 유지하고 나중에 재사용할 수 있다.
>
> ✅ 변화를 감지함.
>
> - 감지는 복제가 가능한 객체를 이전 사본과 비교하고 전체 객체 트리를 돌아야 하는데, 불변 객체에서 변화를 감지하는 것은 상당히 쉽다. 참조하고 있는 불변 객체가 이전 객체와 다르다면 객체는 변한 것이다.
>
> ✅ React에서 다시 렌더링하는 시기를 결정함.
>
> - 불변성의 가장 큰 장점은 React에서 *순수 컴포넌트*를 만드는 데 도움을 준다는 것. 변하지 않는 데이터는 변경이 이루어졌는지 쉽게 판단할 수 있으며 이를 바탕으로 컴포넌트가 다시 렌더링할지를 결정할 수 있다.

- 모 블로그 내용

  > React가 불변성을 지키는 이유는 부모컴포넌트가 
  >
  > re-rendering 되거나 state,props가 변화될 때 렌더링이 일어나게 된다.
  >
  > 
  >
  > 근데 렌더링을 할지 말지 판단하기 위해 state가 변화되는지를 판단한다.
  >
  > 그 과정에서 state 객체 내의 모든 value를 다 깊은 비교하면 당연하게도 효율적이지 않다.
  >
  > 그렇기 때문에 이전 객체와 현재 객체를 얕은 비교로 판단하기 때문에 불변성의 유지가 중요하다.
  >
  >  
  >
  > state를 직접 변경하게 되면 value 값은 바뀌지만 참조 값은 바뀌지 않으므로 렌더링이 일어나지 않는다.
  >
  > mutable한 상태를 사용하게 되면 리액트 돔이 제대로 된 추적을 할 수 없을 것이고,
  >
  > 예기치 않은 사이드 이펙트를 발생시킬 수 있다.
  >
  > 
  >
  > ### 어떻게 불변성을 지킬까?
  >
  > 스프레드 문법, map, filter, slice, reduce 와 같은 새로운 배열을 반환하는 메소드들을 활용한다.
  >
  >  
  >
  > setState를 이용할 때 원시타입 경우에는 값을 바로 넣어주어도 되지만
  >
  > 참조타입인 경우에는 새로운 객체나 배열을 생성한 후 값을 넣어주어야 한다. 

  출처: https://gusehd66.tistory.com/entry/React-React%EA%B0%80-%EB%B6%88%EB%B3%80%EC%84%B1%EC%9D%84-%EC%A7%80%ED%82%A4%EB%8A%94-%EC%9D%B4%EC%9C%A0?category=1216213

---

### 관련 용어

- Element Variables: 리엑트 엘리먼트를 변수처럼 다루는 것.
- Inline Conditions: 조건문을 코드 안에 집어넣는 것. 
  - inline if: **&& 연산자의 사용** 🔥🔥🔥 === **단축 평가**, **short-circuit evaluation** 방식
    👉 결과가 정해져 있는 논리 연산에서 굳이 불필요한 연산을 하지 않기 위해 하는 방법
    👉 컴포넌트를 보여줄지 말지 정할 때 사용.
  - inline if-else: **삼항 연산자(?)의 사용** 🔥🔥🔥
    👉 조건에 따라 각각 다른 컴포넌트를 보여줘야할 때 사용.
    ![image](https://user-images.githubusercontent.com/122634701/216360629-88c99fdd-fd2b-40da-9bfc-c2cc0ddb494f.png)



---

### Component 렌더링 막기 🔥🔥🔥

- nulll을 리턴하면 레더링 되지 않음.
  👉 컴포넌트 생명주기에 영향을 주지 않기 때문에 걱정할 거 없다. 
  👉 예를 들어 componentDidUpdate 잘 호출된다.

| ![image](https://user-images.githubusercontent.com/122634701/216360999-b1076868-0969-4eb8-954c-45d6c3ce1301.png) | ![image](https://user-images.githubusercontent.com/122634701/216361392-fd99782c-d2ff-492a-ad58-26b5506a4d59.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

---

### useEffect ()🔥🔥🔥

![image](https://user-images.githubusercontent.com/122634701/216743528-73df187a-8ff2-4540-9094-1865f55283c2.png)

---

### useMemo()

![image](https://user-images.githubusercontent.com/122634701/216743684-18060fa3-8df3-4a49-a8d1-f105873068c7.png)

- useMemo([create 함수], [의존성 배열])
- create함수는 렌더링이 일어나는 동안 실행된다. 그렇기 때문에 일반적으로 렌더링이 일어나는 동안 실행돼서는 안될 작업을 useMemo 함수에 넣으면 안된다. 예를 들어 useEffect에서 실행돼야 할 side effect같은 것이다. 서버에서 데이터를 받아오거나 수동으로 DOM을 변경하는 작업 등.
- 의존성 배열을 생략할 시 매 렌더링마다 함수가 실행됨 👉 아무런 의미가 없음.
- 의존성 배열을 빈 배열일 경우에는 컴포넌트 마운트 시에만 호출된다.

---

