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

\- 모바일이던 웹이던 항상 **일관성** 있는page를 원함(component 와 pattern을 이용)

#### 우리는 _Theme_과 _Component_라는 개념을 활용할 수 있다

#### (BONUS)

Jakob Nielsen과 Donald Norman은 UX 분야에서 전설적인 인물들. 아샬이 자주 참고한다(이 회사엔 없지만 앨런 쿠퍼도 포함).

* [제이콥 닐슨](https://ko.wikipedia.org/wiki/%EC%A0%9C%EC%9D%B4%EC%BD%A5\_%EB%8B%90%EC%8A%A8) : 사용성 테스트로 유명
  *   ### 웹 사용성

      닐슨은 웹 사용성에 관한 여러 논쟁을 주도하고 있다. 그래픽 디자이너로서의 시각이 아닌 공학 중심적인 시각으로 일부 유명 [웹 사이트](https://ko.wikipedia.org/wiki/%EC%9B%B9\_%EC%82%AC%EC%9D%B4%ED%8A%B8)의 사용성에 대한 엄정한 비판을 하고 있다. 특히 [사용성](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9A%A9%EC%84%B1)을 희생하고 [장애인](https://ko.wikipedia.org/wiki/%EC%9E%A5%EC%95%A0%EC%9D%B8)을 배려하지 않는 많은 사이트들이 [플래시 애니메이션](https://ko.wikipedia.org/wiki/%ED%94%8C%EB%9E%98%EC%8B%9C\_%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98)이나 과도한 그래픽을 사용하는 것에 대해 비판적인 입장을 가지고 있다. 그의 장애인 사용성 연구에서 인터넷은 장애인이 이전에 경험하기 힘들었던 정보에 접근할 수 있는 강력한 도구가 될 수 있음을 확인하였다. 하지만 예를 들어 시각장애인을 위해서는 특수한 보조기구가 필요하고 웹 사이트에서 [접근성](https://ko.wikipedia.org/wiki/%EC%A0%91%EA%B7%BC%EC%84%B1)을 높이기 위한 디자인이 이루어져야지만 일반인처럼 장애인도 사용하기 쉬울 수 있다. 특히 구형의 플래시 애니메이션이나 그림을 많이 사용하는 웹 디자인의 경우 장애인을 위한 [접근성](https://ko.wikipedia.org/wiki/%EC%A0%91%EA%B7%BC%EC%84%B1) 문제가 심각했다. 이러한 문제의 해결을 위한 방법으로는 웹 그래픽 사용시에 대체지문(Alt text,Alternative Text)을 사용하여 그 그래픽의 의미를 알려주어야한다. 또한 사용자가 읽을 필요가 있거나 반응이 필요한 것은 반드시 정지 상태를 유지하여야 한다. 그런것들이 움직임이 있는 상태에서는 시각 장애인과 약시의 문제를 가진 많은 사람들이 불편을 겪게 된다. 또한 관련된 요소들은 가까이 있어야 하며 지나치게 복잡한 기능을 피해야 한다.
  *   ### [반사용성 디자인](https://ko.wikipedia.org/w/index.php?title=%EB%B0%98%EC%82%AC%EC%9A%A9%EC%84%B1\_%EB%94%94%EC%9E%90%EC%9D%B8\&action=edit\&redlink=1)

      놀랍게도 많은 웹들이 [사용자 중심 디자인](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9A%A9%EC%9E%90\_%EC%A4%91%EC%8B%AC\_%EB%94%94%EC%9E%90%EC%9D%B8)이 아닌 오히려 사용성을 의도적으로 떨어뜨리는 디자인을 하고 있다고 한다. 이는 안타깝게도 많은 회사의 웹 디자인을 책임지는 사람들이 [사용성](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9A%A9%EC%84%B1)에 반하는 디자인을 함으로써 회사에게 얻어지는 이익이 있다고 믿으며 그렇게 주장하기 때문이다. 예를 들어 웹디자인 분야에서 사람들이 원하는 것을 찾는 것을 의도적으로 방해함으로써 웹 사이트 내에서 방황하게 되며 이에 따라 [페이지 뷰](https://ko.wikipedia.org/wiki/%ED%8E%98%EC%9D%B4%EC%A7%80\_%EB%B7%B0)가 높아지며 이는 회사의 이익으로 연결되기 때문이다. 대한민국의 대표적인 포털 사이트인 [다음](https://ko.wikipedia.org/wiki/%EB%8B%A4%EC%9D%8C), [야후!](https://ko.wikipedia.org/wiki/%EC%95%BC%ED%9B%84!), [네이버](https://ko.wikipedia.org/wiki/%EB%84%A4%EC%9D%B4%EB%B2%84) 등의 사이트에서 닐슨이 주장한 반사용성 디자인의 예를 찾을 수 있다. 또 다른 예로는 2000년 미국 대통령 선거에서 플로리다주 팜비치 군에서 사용되었던 ‘[나비투표용지](https://ko.wikipedia.org/w/index.php?title=%EB%82%98%EB%B9%84%ED%88%AC%ED%91%9C%EC%9A%A9%EC%A7%80\&action=edit\&redlink=1)’이다. 당시 팜비치군의 선거관리인이었던 테레사 르포어에 의해 디자인된 이 용지는 가운데 구멍을 뚫는 칸을 두고 양쪽에 피선거인들의 명단을 늘어 놓아 유권자로 하여금 의도적으로 실수하게끔 한 것이 아니냐는 의혹을 받기도 했다.[\[1\]](https://ko.wikipedia.org/wiki/%EC%A0%9C%EC%9D%B4%EC%BD%A5\_%EB%8B%90%EC%8A%A8#cite\_note-1)
* [도널드 노먼](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%84%90%EB%93%9C\_%EB%85%B8%EB%A8%BC) : 어포던스 창시자
  * 어포던스(Affordance)는 어떤 행동을 유도한다는 뜻으로 행동유도성이라고도 한다. 어근 어포드(Afford)는 원래 '\~할 여유가 있다, \~하여도 된다, \~을 공급하다, 산출하다'라는 뜻을 가지고 있으나 보통 사전에 없는 뜻으로 인간 컴퓨터 상호작용, 인지 심리학, 산업 디자인, 인터렉션 디자인, 환경 심리학 그리고 인공지능학 분야에서는 '서로 다른 개념을 연결하는 것'이란 뜻으로 쓰이기도 한다. 다시 말해 물건(object)과 생물(organism, 주로 사람) 사이의 특정한 관계에 따라서 제시되는 것이 가능한 사용(uses), 동작(actions), 기능(functions)의 연계 가능성을 의미한다. [https://ko.wikipedia.org/wiki/%EC%96%B4%ED%8F%AC%EB%8D%98%EC%8A%A4](https://ko.wikipedia.org/wiki/%EC%96%B4%ED%8F%AC%EB%8D%98%EC%8A%A4)
* [앨런 쿠퍼](https://en.wikipedia.org/wiki/Alan\_Cooper) : Visual Basic의 아버지, Interaction design 창시자
  *   #### Interaction design and user experience

      Early in his career, Cooper began to critically consider the accepted approach to software construction. As he reports in his first book, he believed something important was missing—software authors were not asking, “How do users interact with this?” Cooper's early insights drove him to create a design process, focused not on what could be _coded_ but on what could be _designed_ to meet users’ needs.[\[18\]](https://en.wikipedia.org/wiki/Alan\_Cooper#cite\_note-18)

      In 1992, in response to a rapidly consolidating software industry, Cooper began consulting with other companies, helping them design their applications to be more user friendly. Within a few years, Alan Cooper had begun to articulate some of his basic design principles. With his clients, he championed a design methodology that puts the users’ needs first. Cooper interviewed the users of his client's products and discovered the common threads that made these people happy. Born of this practice was the use of [_personas_](https://en.wikipedia.org/wiki/Persona\_\(marketing\)) as design tools. Cooper preached his vision in two books.[\[19\]](https://en.wikipedia.org/wiki/Alan\_Cooper#cite\_note-19) His ideas helped to drive the [user experience](https://en.wikipedia.org/wiki/User\_experience) movement and define the craft that would come to be called “[interaction design](https://en.wikipedia.org/wiki/Interaction\_design).”

      Cooper's best-selling first book, _About Face: The Essentials of User Interface Design,_ was first published in 1995. In it, Cooper introduces a comprehensive set of practical design principles, essentially a taxonomy for software design. By the second edition, as the industry and profession evolved, “interface design” had become the more precise “interaction design.” The basic message of this book was directed at programmers: Do the right thing. Think about your users.[\[20\]](https://en.wikipedia.org/wiki/Alan\_Cooper#cite\_note-20) The book is now in its fourth edition, entitled _About Face: The Essentials of Interaction Design_, and is considered a foundation text for the professional interaction designer. Cooper introduced the ideas of software [application posture](https://en.wikipedia.org/wiki/Application\_posture) such as a "sovereign posture" where an application uses most of the space and waits for user input or a "transient posture" for software that does not run or engage with the user all the time. With websites he discusses "informational" and "transactional" postures in _About Face_.

      In his 1998 book, _The Inmates Are Running the Asylum: Why High-Tech Products Drive Us Crazy and How to Restore the Sanity_, Alan Cooper outlined his methodology, called Goal-Directed design, based on the concept that software should speed the user towards his or her ultimate goal rather than ensnare him or her in computer minutiae.[\[21\]](https://en.wikipedia.org/wiki/Alan\_Cooper#cite\_note-21) In the book, Cooper introduced a new concept that he called _personas_ as a practical interaction design tool. Based on a brief discussion in the book, personas rapidly gained popularity in the software industry[\[22\]](https://en.wikipedia.org/wiki/Alan\_Cooper#cite\_note-22) due to their unusual power and effectiveness. Today, the concepts of interaction design strategy and the use of personas have been broadly adopted across the industry. Cooper directs the message of his second book to the businessperson: know your users’ goals and how to satisfy them. You need interaction design to do the thing right. Cooper advocates for integrating design into business practice in order to meet customer needs and to build better products faster by doing it right the first time.

      Alan Cooper's current focus is on how to effectively integrate the advances of interaction design with the effectiveness of [agile software development](https://en.wikipedia.org/wiki/Agile\_software\_development) methods. Cooper regularly speaks and blogs about this on his company's website.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p> <a href="https://www.nngroup.com/articles/design-systems-101/">Nielsen Norman Group의 “Design Systems 101”</a></p></figcaption></figure>

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
