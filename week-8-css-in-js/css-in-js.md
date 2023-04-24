# CSS in JS

#### 학습 키워드

* CSS in JS 란
* CSS

> 💡 CSS 를 잘 사용하기 위해선 CSS 자체에 대해서 잘 알고 있어야 합니다. 레퍼런스를 참고하여 CSS 를 정리해봅시다. 스타일 자체는 굉장히 많기 때문에 자주 사용하는 것들 위주로 찾아서 정리하시면 좋습니다. 특히나 선택자, 박스모델, media query, Flexbox, Grid 정도는 필수적으로 알고 계셔야 합니다.&#x20;
>
> 참고 레퍼런스:&#x20;
>
> \- [https://developer.mozilla.org/ko/docs/Web/CSS/Reference](https://developer.mozilla.org/ko/docs/Web/CSS/Reference)&#x20;
>
> \- [flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)&#x20;
>
> \- [Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

## CSS-in-JS

\|  [CSS-in-JS](https://en.wikipedia.org/wiki/CSS-in-JS)

\|  [React: CSS in JS (2014)](https://blog.vjeux.com/2014/javascript/react-css-in-js-nationjs.html)

1. Global Namespace
2. Dependencies
3. Dead Code Elimination
4. Minification
5. Sharing Constants
6. Non-deterministic Resolution
7. Isolation

\|  [A Unified Styling Language (2017)](https://blog.rhostem.com/posts/2017-06-24-unified-styling-language)

1. Scoped styles
2. Critical CSS
3. Smarter optimisations
4. Package management
5. Non-browser styling

\|  [All You Need To Know About CSS-in-JS (2017)](https://d0gf00t.tistory.com/22)

1. Thinking in components
2. CSS-in-JS leverages the full power of the JavaScript ecosystem to enhance CSS
3. True rules isolation
4. Scoped selectors
5. Vendor Prefixing
6. Code sharing
7. Only the styles which are currently in use on your screen are also in the DOM (react-jss)
8. Dead code elimination
9. Unit tests for CSS

\|  [Most popular CSS-in-JS libraries](https://npmtrends.com/aphrodite-vs-emotion-vs-glamorous-vs-jss-vs-radium-vs-styled-components-vs-styletron)

→ 2023년 1월 기준으로 styled-components, JSS, Emotion 순서

## 성능 이슈

\|  [CSS-in-JS와 성능 (2021)](https://hyeonseok.com/blog/877)

→ CSS 파일과 JS 파일 로딩의 차이

\|  [Why We're Breaking Up with CSS-in-JS (2022)](https://bit.ly/3g6QufF)

대안:

* [Linaria](https://linaria.dev/)
  * CSS를 평범한 텍스트로 작성
  * React에 종속적이지 않지만, React Styled Component도 지원함
* [vanilla-extract](https://vanilla-extract.style/)
  * CSS를 오브젝트 형태로 표현. React의 Inline Style과 유사함
  * React와 무관하게 사용 가능





