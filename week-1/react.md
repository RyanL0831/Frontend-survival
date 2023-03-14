# React

## 학습 키워드

* React란?
* React 컴포넌트
* React 리렌더링
* IoC(Inversion of Control)
* Library vs Framework

## React

[**React 공식문서**](https://ko.reactjs.org/) [**React Beta 문서**](https://beta.reactjs.org/)

* React로 작업하는 프로세스는 [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)를 참고.
* React는 선언적 프로그래밍으로 UI를 구현할 수 있게 하며, UI를 어떻게 보여줄지 React에게 전달하면 됨. 명령형 프로그래밍 대신 직접 DOM을 조작하지 않아도 됨.
* React에서 UI를 개발할 때, 먼저 컴포넌트로 조각내고 각각에 적합한 상태를 작성함. 그리고 컴포넌트를 연결하여 데이터가 흐르게 하여 UI를 완성함. 이를 활용하여 제품 검색이 가능한 데이터 테이블을 만들기 가능함.

## UI를 컴포넌트 단위로 쪼갠다

UI 개발을 시작하기 위해서는 목업을 기반으로 각 컴포넌트와 서브 컴포넌트에 네모 박스를 그리고 이름을 붙임. 만약 디자이너와 함께 협업한다면, 이미 디자인 툴에서 컴포넌트 이름이 붙여져 있을 수도 있음. UI 디자인을 컴포넌트로 분리하는 다양한 방법들을 배경 지식에 따라 고려해볼 수 있음.

* Programming: 함수 혹은 객체를 생성해야 하는지 결정하는 방식과 똑같다. 단일책임원칙이며 즉 컴포넌트는 이상적으로 한 가지의 일만 해야 한다. 만약 컴포넌트가 커지면, 작은 서브 컴포넌트들로 분리되야함.
* CSS: 무엇을 class selector로 만들지 판단.
* Design: 디자인 레이어를 어떻게 구성할지 판단.

잘 구조화된 JSON 데이터라면, UI와 컴포넌트 구조를 매핑하기 쉬울 것. UI와 데이터 모델은 종종 유사한 아키텍처와 모양을 가지기 때문. 각각의 컴포넌트가 데이터 모델의 한 부분과 매치되도록 UI를 컴포넌트로 분리함.

* FilterableProductTable
  * SearchBar
  * ProductTable
    * ProductCategoryRow
    * ProductRow

## React를 정적 버전으로 만든다

* 컴포넌트를 계층으로 구분하고, UI를 작성하기 전에는 데이터 모델을 이용하여 기능 없는 UI를 작성하는 것이 가장 간단한 접근 방식. 일반적으로 UI를 먼저 작성하고 기능을 추가하는 것이 더 쉬운데, 이는 UI 작성에는 많은 타이핑이 필요하지만 생각이 많이 필요하지 않고, 기능 추가에는 생각이 많이 필요하지만 타이핑은 많지 않기 때문.
* Props는 부모에서 자식으로 데이터를 전달하는 방법이며, State는 오직 상호작용을 위한 데이터를 다루는 것이다. UI를 작성할 때는 State는 필요하지 않다.컴포넌트를 작성할 때는 top down 방식과 bottom up 방식이 있다. 간단한 어플리케이션은 일반적으로 top-down 방식이 쉽고, 규모가 있는 어플리케이션은 bottom-up 방식이 쉽다.

컴포넌트를 작성한 후에는 재사용 가능한 컴포넌트가 생성되며, 데이터 모델을 렌더링하는 최상위 컴포넌트는 prop으로 데이터 모델을 받게됨. 이것은 데이터가 최상위 레벨 컴포넌트로부터 가장 바닥에 있는 컴포넌트까지 위에서 아래로 단방향으로 흐르는 "one-way data flow" 방식. 이러한 구조에서 컴포넌트는 JSX만 반환하므로, 애플리케이션은 정적인 상태를 유지하게됨.

## 적절한 UI state를 찾는다

* UI 상호작용을 위해 state를 사용하여 데이터 모델을 변경할 수 있어야함. state는 어플리케이션에서 최소한으로 필요한 데이터의 집합이며 DRY(don't repeat yourself) 원칙을 따라야함. 따라서 필요한 값들만 state로 만들고 나머지는 state를 이용한 연산으로 처리해야함. 예를 들어, 쇼핑 리스트에서 아이템을 저장할 때는 배열 state를 사용하고, 리스트에 담긴 아이템의 개수를 표시할 때는 배열의 길이를 이용하여 state를 이용한 연산으로 표현해야함.
* 사용되는 내내 값이 변하지 않는다면 state가 아님.
* props를 통해 부모로부터 전달받는다면 state가 아님.
* 컴포넌트 내에 이미 존재하는 state나 props를 이용하여 계산할 수 있다면 특히 state가 아님.

## 렌더링

* 브라우저에 view를 보여주는 것
* 함수가 실행되는 것
* createRoot (React 18)

```ts
function Greeting() {
  return <p>Hello, world!</p>;
}
function main() {
  const element = document.getElementById('root');
  if (!element) {
    return;
  }
  const root = ReactDOM.createRoot(element);
  root.render(<Greeting />);
}
main();
```

* 여러 개의 Root를 만들 수 있고, 여러 번 render 가능.
* React는 변경된 부분만 업데이트함.
  * Reconciliation(재조정)

## 리렌더링

State가 바뀔 때 리렌더링이 되고, 자녀들도 리렌더링이 됨.

## Component는 최상위에 하나의 부모가 있어야함.

* React.createElement
  * jsx가 js로 변환될 때 위 메소드를 실행함. 첫 번째 인자로 태그 혹은 컴포넌트를 1개 받음.
* Fragment
  * DOM에 렌더링이 될 때 사라지는 태그, 코드 작성시 부모 태그의 역할을함.
