# React Component

## 학습 키워드

* Rest API 와 GraphQL
  1. REST API 란 무엇인가
  2. GraphQL은 왜  등장했는가?
  3. REST API vs GraphQL
* JSON
* DSL (Domain-Specific Language)
* 선언형 프로그래밍
* 명령형 프로그래밍
* SRP (단일  책임 원칙)
* Atomic Design
* React component 와 props



## 데이터

B/E에서 JSON 형태의 데이터를 돌려주는 API를 제공한다고 가정(대부분은 REST API 또는 GraphQL)

### REST API

* GET, POST, PUT/PATCH, DELETE (CRUD)
* Resource 중심

### GraphQL

* Graph 자료 구조
* Query에서 얻고자 하는 걸 지정
* Query(Read), Mutation(Command: Create, Update, Delete), Subscription(Event)

### JSON API

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### JSON.stringify() : 객체를 매개변수로서 수용하고, JSON 문자열 형태로 변환합니다.Object를 문자열로 반환

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### JSON.parse() : JSON 문자열을 매개변수로서 수용하고, 일치하는 자바스크립트 객체로서 변환합니다.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

F/E는 이 데이터를 사용자가 볼 수 있도록 UI를 구성한다. React는 선언형(HTML과 유사한 모양의 DSL을 사용)으로 UI를 구성할 수 있다.

DSL: Domain 특화 언어 - 특정 도메인에 해당하는 문제를 쉽게 푸는 언어 (ex. Web - HTML)

## 컴포넌트 계층 구조

### React의 강력한 특징 둘 중 하나:

* “Component-Based”
* “Build encapsulated components that manage their own state, then compose them to make complex UIs.”

#### Component를 모아모아 복잡한걸 만듬 (component는 복잡하면 안됨 심플해야함)

#### 몇 가지 기준:

* [SRP (Single Responsibility Principle) 단일책임원칙](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%B1%85%EC%9E%84\_%EC%9B%90%EC%B9%99)
  * 컴포넌트가 너무 커지고 있다면...
* CSS → 이미 알고 있는 기준을 재활용
* Design’s Layer
* **Information Architecture (JSON Schema의 영향) → 실제로 엄청 많이 쓰게 됨. 자연스러운 SRP를 위해서 사실상 강제됨 (백엔드에서 재가공을 많이함, GraphQL에서는 자동으로 해줌)**&#x20;

작은 컴포넌트=부품을 만들어서 조립. 조합은 가지수를 폭발적으로 늘릴 수 있는 가장 전형적인 방법

[Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/)은 우리가 잘 알고 있는 계층형 구조를 몇 가지 카테고리로 묶은 방법











