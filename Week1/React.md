# 학습 키워드

- React란?
- React 컴포넌트
- React 리렌더링
- IoC(Inversion of Control)
- Library vs Framework

## React

<aside>

[**React 공식문서**](https://ko.reactjs.org/)

→ 옛날 거라서 보면 안 될 줄 알았는데, 최근에 업데이트가 됨.

- 기존에는 클래스 컴포넌트 예제가 많았지만, 많은 부분이 함수 컴포넌트로 변경되어 읽기에 괜찮다.

[**React Beta 문서**](https://beta.reactjs.org/)
→ 요즘 React 사용법을 다룬 문서. 베타 버전이고 완성도가 낮지만 (+ 한국어 버전이 없지만) 이것부터 읽는 걸 권장.

</aside>

- React로 작업하는 프로세스는 [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)를 참고. “상태”를 골라내는 게 핵심이다.  
  React는 직접 DOM을 찾아서 속성을 추가하고 element를 추가하는 명령형 프로그래밍이 아닌 선언적 프로그래밍을 할 수 있게 해준다. 화면에 UI를 어떻게 보여주고 싶은지 React에게 전달하면 된다.  
  React로 UI(User Interface)를 개발할 때 먼저 Component(컴포넌트)라고 불리는 조각들로 쪼개야 합니다. 그 후에 각각의 컴포넌트마다 적합한 state를 작성합니다. 마지막으로 컴포넌트들을 함께 연결하여 컴포넌트를 통해 데이터가 흐르게 합니다. 아래에서는 React를 이용하여 제품 검색을 할 수 있는 데이터 테이블을 만드는 과정에 대해 생각해볼것  
  먼저 데이터(JSON)와 디자인 목업을 전달받았다고 가정한다.  
  React에서 UI를 구현하기 위해서는 일반적으로 5가지 스텝을 밟게 된다.

### Step 1: UI를 컴포넌트 단위로 쪼갠다

목업의 컴포넌트와 서브 컴포넌트에 네모 박스를 그리고 각각 이름을 붙이는 것으로 시작한다. 만약 디자이너와 함께 협업한다면, 이미 디자인 툴에서 컴포넌트에 붙여놓은 이름이 있을 수도 있다.  
배경 지식에 따라 디자인을 컴포넌트로 분리하는 다양한 방식을 생각해볼 수 있다.

- Programming: 함수 혹은 객체를 생성해야 하는지 결정하는 방식과 똑같다. 단일책임원칙(SRP)이며 즉 컴포넌트는 이상적으로 한 가지의 일만 해야 한다. 만약 컴포넌트가 커지면, 작은 서브 컴포넌트들로 분리되어야 한다.
- CSS: 무엇을 class selector로 만들지 고려한다.
- Design: 디자인 레이어를 어떻게 구성할지 고려한다.

만약 JSON이 잘 구조화되어 있다면, UI와 컴포넌트 구조를 자연스랩게 매핑할 수 있다. 왜냐하면, UI와 data model은 종종 같은 아키텍처, 같은 모양을 가진다. 각각의 컴포넌트가 data model의 한 조각과 매치되도록 UI를 컴포넌트로 분리한다.
![github pr](./images/react-step1.png)
ProductTable의 Name과 Price가 컴포넌트가 아닌 것은 취향의 차이다. 컴포넌트로 만들어도 괜찮다. 지금은 괜찮지만 정렬 기능이 추가되는 등 헤더가 복잡해지면, 그때는 ProductTableHeader 컴포넌트를 작성하는 게 합당할 것이다.  
현재 목업으로부터 컴포턴트를 식별했고 분리하면서 정리했다. 목업에서 다른 컴포넌트 내부에 등장하는 컴포넌트는 계층적으로 자식으로 등장해야 한다.

- FilterableProductTable

  - SearchBar
  - ProductTable
    - ProductCategoryRow
    - ProductRow

### Step 2: React를 정적 버전으로 만든다

컴포넌트를 계층으로 구분했고, 이제는 app을 구현할 시간이다.  
가장 간단한 접근 방식은 기능은 추가하지 않고 data model를 이용하여 UI를 작성하는 것이다 (마크업, 퍼블리싱)  
보통 UI를 먼저 작성하고 기능을 추가하는 게 쉽다.  
왜냐하면 UI를 작성하는 것은 많은 타이핑이 필요하지만 생각은 하지 않아도 되고 기능을 추가하는 것은  
생각은 많이 필요하지만 타이핑은 많지 않기 때문이다.

Props는 부모에서 자식으로 데이터를 전달하는 방법이다.  
State는 오직 상호작용을 위한, 즉 항상 데이터가 바뀌는 것이다.  
UI를 작성할 때는 state는 필요없다.

컴포넌트를 작성할 때 `top down` 방식과 `bottom up` 방식이 있다.  
간단한 어플리케이션은 일반적으로 `top-down` 방식이 쉽고 규모가 있는 어플리케이션은 `bottom-up` 방식이 쉽다.

컴포넌트를 작성한 후에는 데이터 모델을 렌더링하는 재사용 가능한 컴포넌트가 생기게 된다.  
왜냐하면 정적 app이라서 컴포넌트는 JSX만 return하기 때문이다.  
최상위 컴포넌트는 prop으로 데이터 모델을 받게 될 것이다.  
이것은 one-way data flow(단방향 데이터 흐름)라고 불리는데
데이터가 최상위 레벨 컴포넌트로부터 가장 바닥에 있는 컴포넌트 까지 위에서 아래로 흐르기 때문이다.

### Step 3: 적절한 UI state를 찾는다

UI를 상호작용할 수 있게 만들기 위해서 사용자가 데이터 모델을 변화시킬 수 있도록 하는것이 필요하다.  
이를 위해서 state를 사용할 것이다.

state는 데이터를 변화시키기 위해서 app에서 기억하고 있어야 하는 최소한의 집합이다.
state를 작성하기 위한 가장 중요한 원칙은 DRY (Don't Repeat Yourself).  
어플리케이션에서 필요한 최소한의 값만 state로 만들고 그 이외의 것들은  
필요에 따라 state를 이용한 연산으로 사용해야 한다.
예를 들어, 쇼핑 리스트를 만들고 있다고 하면 아이템을 state 배열에 저장할 수 있다.  
만약 리스트에 담긴 아이템의 개수를 표현하고 싶다면, 또 다른 state에 아이템 개수를  
저장하는 것이 아니라 state 배열에서 길이를 이용해야 한다.

이제 예제 어플리케이션에서 데이터들을 생각해보자.

1. 제품의 원본 리스트
2. 유저가 입력한 검색어
3. 체크박스의 값
4. 필터된 제품 리스트

이중에 무엇이 state일까? 아래에 해당하지 않는것을 찾아보자.

- 사용되는 내내 값이 변하지 않는다면 state가 아니다.
- props를 통해 부모로부터 전달받는다면 state가 아니다.
- 컴포넌트 내에 이미 존재하는 state나 props를 이용하여 계산할 수 있다면 특히 state가 아니다.

해당하지 않는것들은 state가 될 것이다.

하나씩 살펴보자.

1. 제품의 원본 리스트는 props로 전달받기 때문에 state가 아니다.
2. 검색어는 계속 변하고, 무언가로 부터 계산할 수 없기 때문에 state로 보인다.
3. 체크박스의 값도 마찬가지로 계속 변하고, 무언가로부터 계산할 수 없기 때문에 state로 보인다.
4. 필터된 제품 리스트는 상태가 아니다. 왜냐하면 제품의 원본 리스트와 검색어, 체크박스의 값으로 계산할 수 있는 값이기 때문이다.

즉 검색어와 체크박스 값만 state인 것을 확인할 수 있다.

---

- 한국어로 읽고 싶다면 [예전 문서의 설명](https://ko.reactjs.org/docs/thinking-in-react.html)만 살짝 참고하자(코드는 참고하지 말 것!).
- [React 코어 개발자가 쓴 React에 대한 이해를 돕는 글](https://overreacted.io/ko/react-as-a-ui-runtime/) (필독!)
  - Dan Abramov는 신이야...

### 렌더링

- 브라우저에 view를 보여주는 것
- 함수가 실행되는 것

- createRoot (React 18)

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

- 여러 개의 Root를 만들 수 있고, 여러 번 render할 수 있다.
- React는 변경된 부분만 업데이트 한다.
  - Reconciliation(재조정)
  - diffing algorithm

### 리렌더링

State가 바뀔 때 리렌더링이 되고, 자녀들도 리렌더링이 된다.

- [React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://velog.io/@surim014/react-rerender)
- [왜 리액트에서 리렌더링이 발생하는가.](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EC%99%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%97%90%EC%84%9C-%EB%A6%AC%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94%EA%B0%80-74dd239b0063)
- [React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)

### Component는 최상위에 하나의 부모가 있어야 한다.

- React.createElement
  - jsx가 js로 변환될 때 위 메소드를 실행한다. 첫 번째 인자로 태그 혹은 컴포넌트를 1개 받는다.
- Fragment
  - DOM에 렌더링이 될 때 사라지는 태그, 코드 작성시 부모 태그의 역할을 한다.

### 보너스

[면접 때 종종 나오는 (쓸모 없는) 질문인 “React는 프레임워크인가요, 라이브러리인가요?”에 대한 React 개발자의 답변](https://twitter.com/trueadm/status/1194567962784653312)

[제어의 역전](https://martinfowler.com/bliki/InversionOfControl.html)(IoC: Inversion of Control)이 Framework의 주요한 특징이고, React는 IoC를 통해 상태와 업데이트가 얽힌 복잡한 상황을 간단히 선언형 UI로 구성하는 혜택을 누린다(이게 바로 React의 첫 번째 특징이다). 그 누구도 매번 root를 render하는 방식으로 쓰면서 “이게 라이브러리지!”라며 감탄하지 않는다.

하지만 일반적으로는 (Martin Fowler의 개탄처럼) IoC는 IoC 컨테이너와 엮여서 DI와 동의어처럼 쓰이고, Next.js, Remix 같은 걸 Framework이라고 부르니 면접 때 괜히 이런 걸로 싸우지는 말자. “리액트 개발자가 이렇게 이야기했다니까요!”라고 해봐야 서로 감정만 상할 뿐이다.

우리는 스스로 몰랐더라도 라이브러리, 프레임워크를 사용하면서 제어의 역전을 경험하고 있다.  
스스로 관리하지 않더라도 구현체에 값을 전달해주면, 구현체가 대신해서 특정 역할을 해주는 것.  
React의 선언적인 렌더링도 제어의 역전이다.