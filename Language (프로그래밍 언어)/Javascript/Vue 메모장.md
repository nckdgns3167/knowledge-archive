# Vue 메모장

---

### CLI 2.x vs CLI 3.x

- 명령어
  - vue init [프로젝트 템플릿 이름] [파일위치]
  - vue create [프로젝트 이름]
- 웹팩 설정 파일 (webpack.config.js)
  - 노출 O
  - 노출 X
- 프로젝트 구성
  - 깃헙의 템플릿 다운로드 (webpack-simple), npm install 명령어 실행해줘야 node_modules 생김.
  - 플러그인 기반으로 기능 추가 (유연해짐)
- ES6 이해도
  - 필요 X
  - 필요 O

---

### Vuex ?

![vuex](https://user-images.githubusercontent.com/122634701/214346624-e4c3d4ab-50e5-48d5-a487-5577fd7ea490.png)

- **모든 구성 요소에 대한 중앙 집중식 저장소 역할**
- Vue.js 애플리케이션을 위한 **상태 관리 패턴 + 라이브러리**
- 상태가 예측 가능한 방식으로만 변경될 수 있도록 하는 규칙을 사용
- 컴포넌트가 많은 중대형 규모의 SPA 에서 유용하다.
- Vuex 의 상태는 메모리에 저장되는 것이기 때문에 새로 고침시 초기화 된다.
- 상태를 새로고침 시에도 유지 하고 싶다면, **vuex-persistedstate**(state - localstorage 동기화 라이브러리) 같은 또 다른 라이브러리가 필요하다.
- **핵심 속성**
  - **state**
  - **getters**
  - **mutations**
  - **actions**
  - **modules**

- 📢 컴포넌트에는 여전히 로컬 상태(data())에 있을 수 있다. Vuex를 사용한다고 해서 모든 상태를 store에 넣을 필요는 없다.
- Vuex 는 **단일 상태 트리(single state tree)** 를 사용하기 때문에 이 집합 내에서 현재 상태를 쉽게 찾을 수 있다. 하나의 어플리케이션은 하나의 store만 가진다는 것을 의미한다.
- state와 getters는 computed에, mutations와 actions는 methods에 작성된다.

---

**Vue.config.productionTip = false ?**

- Vue 앱이 처음 실행 될 때 나오는 경고문(배포에 대한 팁)을 출력할지 말지 정하는 것.
- default는 false 

---

**render: h => h(App)은 ES6 문법이 적용된 것이다.**

```vue
// #1
render: function (createElement) {
    return createElement(App);
}

// #2
render (createElement) {
    return createElement(App);
}

// #3
render (h){
    return h(App);
}

// #4
render: h => h(App);
```

- render는 실질적으로는 createElement()의 반환값이다. createElement()는 Virtual DOM(가상 돔)을 만들어 렌더링하는 함수이다.
- h 는 hyperscript의 약자로 HTML 구조를 생성하는 스크립트를 의미함.

---



