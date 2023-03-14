# Testing Library

* Jest
* Describe-Context-It 패턴
* React Testing Library

**Jest**

[**Jest 공식문서**](https://jestjs.io/)

Mocha와 Chai처럼 RSpec의 describe-it을 지원(describe-context-it). Mocking도 다양한 레벨에서 쉽게 사용가능.

**기본 테스트 코드**

* 테스트 코드의 변화를 계속 반영하려면,
* npx jest --watchAll
* 테스트를 먼저 짜고 구현부를 구성 -> TDD (Test Driven Development)

```ts
function add(x: number, y: number): number {
  return x + y;
}
test('add', () => {
  expect(add(1, 2)).toBe(3);
});
```

**BDD 스타일의 테스트 코드**

* 표현력이 좋아지고, 사고를 하게 만듬.
* 행동을 묘사한다.

```ts
describe('add', () => {
  it('returns sum of two numbers', () => {
    expect(add(1, 2)).toBe(3);
  });
});
```

**context 사용하기 (D-C-I Pattern)**

```ts
const context = describe;
describe('add 함수는', () => {
  context('두 개의 양수가 주어졌을 때', () => {
    it('두 숫자의 합을 돌려줌.', () => {
      expect(add(1, 2)).toBe(3);
    });
  });
});
```

* npx jest --verbose
  * 테스트 코드의 설명이 조금 더 자세하게 나온다

**React Testing Library**

* [**React Testing Library 공식문서**](https://testing-library.com/docs/react-testing-library/intro)
* [**jest-dom**](https://testing-library.com/docs/ecosystem-jest-dom/)

UI 테스트에 특화된 라이브러리. E2E Test(PlayWright, Cypress)처럼 사용 가능.

단, “F/E 테스트 = only React 컴포넌트 테스트”가 되는 상황은 최대한 피하는 게 좋음. 불필요한 많은 테스트 코드를 작성할 위험이 있음. 유지보수를 돕기 위해 테스트 코드를 작성하는데, 테스트 코드를 잘못 작성하면 오히려 유지보수를 저해할 가능성이 있음.

참고 영상:

* [프론트엔드(Front-end)도 테스트해야 하나요?](https://youtu.be/-kUmsKRmOnA)
* [Mocking 때문에 테스트 코드를 작성하기 어렵나요](https://youtu.be/RoQtNLl-Wko)

**간단한 테스트 코드**

```tsx
test('Greeting', () => {
  render(<Greeting name="world" />);
  screen.getByText('Hello, world!');
  screen.getByText(/Hello/);
  expect(sceen.queryByText(/Hi/)).not.toBeInTheDocument();
});
```

***

* 요구사항을 명확히 하는 것
* 명세를 명확하게 하기
  * 버그를 잡기 제일 좋은 시점은 코딩을 하기 전, 명세를 보고 빠진 부분이 있는지 확인
* 명세를 따라 설계를 한다.
  * 아주 작은 여러 단계로 쪼개기
  * 코딩을 하면서 배우게 된다. 설계가 맞았는지 틀렸는지.
  * 설계를 개선하게 된다, 개선된 설계에 따라 다시 코딩을 함.

어떤 문제를 해결하려고 했었는지 요구사항을 명확하게 하는 것이 가장 중요.

***

목표

1. Specific (구체적)
2. Measurable (측정 가능)
3. Attainable (달성 가능)
4. Realistic (현실적)
5. Timely (기간)

목표를 쓰기, 이 목표들을 잘게 나눠서 목록으로 만들기. 그리고 하나씩 실행
