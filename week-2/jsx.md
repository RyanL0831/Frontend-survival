# JSX

* React에서 JSX를 사용하는 목적
* Syntactic sugar
* React.createElement
* React Element
* React StrictMode
*   VDOM(Virtual DOM)이란?

    \- DOM이란?

    \- DOM과 Virtual DOM의 차이
* Reconciliation(재조명) 과정은 무엇인가?

## JSX Introduction:

JSX is an XML-like syntax extension to ECMAScript(JS)

XML 같은 문법 확장

* React의 부산물, VueJS 등 여러곳에서 사용 가능
* JS code와 1대1 매칭
* TypeScript, Babel, SWC 등으로 변환 가능

\* VScode 시초: Atom texteditor(made by github) -> Electron 출시 -> VScode(MS) -> Github 인수(by MS) -> Atom 폐지

\* HTML + XML => XHTML (HTML5 출시 후 소멸중)

\* React.createElement == React의 namespace

```markup
<p>
Hello, World! <br>   -> </br> 로 변환필요 (HTML과 JSX의 차이)
</p>
```

## Babel presets:

"Presets"에서 "React" 체크 OR "Plugins"에서 "@babel/plugin-transform-react-jsx"를 추가

JSX 파일에 /\* @jsx XYZ \*/ 주석을 추가하면 React.createElement 대신 "XYZ"를 쓰게 된다

## Example #1

// JSX 파일

```jsx
<p>Hello, world!</p>
```

// 변환된 JS 코드

```javascript
React.createElement("p", null, "Hello, world!");
```

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## \<React.Fragment> 묶음

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Fragment를&#x3C;> &#x3C;/> 이렇게도 표현 가능</p></figcaption></figure>



## 0:46:30 - React Strict Mode:

```markup
<React.StrictMode>                    <>
  <App />                OR         <App />
</React.StrictMode>                   </>
```

## VDOM(virtual DOM)을 쓰는 이유

DOM 보다 빠르기는 하지만 유지보수 측면에서 월등함

## VDOM(virtual DOM)의 혜택

일단 다 넣는다 -> 신규로 생성된 VDOM & 기존의 DOM 이 존재

Tree 두개를 비교 -> 선언적 API 가능 (핵심Idea: 적절한 빠르기 + 유지보수 기능)

```
VDOM      DOM
홍    1    홍
기    2    길 -> 기 ()
동    3    동
```

## jquery의 단점:

일일이 하나하나 다 selector를 찾아서 고쳐줘야함

## 최적화 하는 방법

1. DevTools로 profiling
2. 긴 목록 가상화: 화면에 긴(ex 만줄짜리) 목록 by DOM -> 화면에 보이는 일부분만 rendering by slice
3. key를 잡아줌: 중복된 값들을 둔 상태로, 빠진것과 새로 추가된 것만 업데이트

## 최적화에 반응하는 올바른 접근방법

* 왜 그렇게 되지?
* 의도, 목적이 뭐지?

