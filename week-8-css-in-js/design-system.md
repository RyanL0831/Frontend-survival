# Design System

#### 학습 키워드

* 반응형 웹 디자인(Responsive web design)
* 디자인 시스템(Design System)
* Atomic Design

## Design System

\|  [Laura Kalbag의 “Design Systems” 소개](https://24ways.org/2012/design-systems/)

\|  [Laura Kalbag의 “Design Systems” 슬라이드](https://speakerdeck.com/laurakalbag/design-systems-1)

\|  [Nielsen Norman Group의 “Design Systems 101”](https://www.nngroup.com/articles/design-systems-101/)

> 👉 Summary: A design system is a set of **standards** to manage design **at scale** by **reducing redundancy** while creating a **shared language** and **visual consistency** across different pages and channels.
>
> Definition: A design system is a complete set of standards intended to manage design at scale using **reusable components and patterns**.

\- 모바일이던 웹이던 항상 일관된 page를 원함(component 와 pattern을 이용)

#### 우리는 _Theme_과 _Component_라는 개념을 활용할 수 있다

#### (BONUS)

Jakob Nielsen과 Donald Norman은 UX 분야에서 전설적인 인물들. 아샬이 자주 참고한다(이 회사엔 없지만 앨런 쿠퍼도 포함).

* [제이콥 닐슨](https://ko.wikipedia.org/wiki/%EC%A0%9C%EC%9D%B4%EC%BD%A5\_%EB%8B%90%EC%8A%A8) : 사용성 테스트로 유명
* [도널드 노먼](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%84%90%EB%93%9C\_%EB%85%B8%EB%A8%BC) : 어포던스 창시자
* [앨런 쿠퍼](https://en.wikipedia.org/wiki/Alan\_Cooper) : Visual Basic의 아버지, Interaction design 창시자

### 사례

* [Atlassian Design System](https://atlassian.design/)
  * brand 기반 design
  * Components tab에 Avatar group -> stack -> 코드 소스 예시
* [Material Design (Google)](https://material.io/)
  * Components 예시 사용
* [Base Web (Uber)](https://baseweb.design/)
  * React에서 사용 가능한 UI components 제공
* [Polaris (Shopify)](https://polaris.shopify.com/)
  * 국내에서는 저명하지만, 해외에서는 영향력있음
* [Lightning Design System (Salesforce)](https://www.lightningdesignsystem.com/)
  * 외국에서 영향력 있음
  * Components -> Accordion 아코디언
  * 일방된 방식 (통일성이 중요)
* [Mailchimp Pattern Library](https://ux.mailchimp.com/patterns)
  * 예전 design system 사례로 유명했음
  * 케릭터의 성격이 항상 들어가 있음
* [Ant Design](https://ant.design/)
  * Figma 피그마와 상용 가능
  * antforfigma.com

### Gallery&#x20;

* [Design Systems Gallery](https://designsystemsrepo.com/design-systems/)
  * 다른 회사들 예시 모음
* [Design Systems](https://www.designsystems.com/open-design-systems/)
  * 타 디자인 예시 모음집

### Atomic Design

\|  [Atomic Design 소개 글](https://bradfrost.com/blog/post/atomic-web-design/)

\|  [Atomic Design 전자책](https://atomicdesign.bradfrost.com/)

#### Atomic design is methodology for creating design systems

* 디자인 시스템을 만들기 위한 방법론
* 가장 작은 단위의 원소 부터 분자 단위로 결합 후 조직화
* 구조 체계에 대해 강박관념을 갖을 필요는 없음, 전체적인 flow를 익히는게 중요! 너무 atomic에 집중하면 refactoring 가능성을 막을수도 있음
* Atoms -> Molecules -> Organisms -> Templates -> Pages
