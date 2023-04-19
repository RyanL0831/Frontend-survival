# usehooks-ts

학습 키워드

* usehooks-ts
  * useBoolean
  * useEffectOnce
  * useFetch
  * useInterval
  * useEventListener
  * useLocalStorage
  * useDarkMode
* swr
* react-query

## usehooks-ts

\| [usehooks-ts](https://usehooks-ts.com/)

TypeScript로 만들었고, JS에서도 사용 가능



모든 Hook에 대한 코드가 웹 사이트에 직접 노출됨

```bash
npm i usehooks-ts
```

#### [useBoolean](https://usehooks-ts.com/react-hook/use-boolean)

참/거짓을 다룰 땐 toggle 같이 의도가 명확한 함수를 쓰는 게 좋다

→ 위에서 만든 TimerControl에 써보자

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

#### [useEffectOnce](https://usehooks-ts.com/react-hook/use-effect-once)

_사용하면 표현력이 좋아짐_

의존성 배열을 빈 배열로 넣어서 한 번만 실행하는 Effect를 잡아줄 때가 많은데, 이걸 쓰면 더 명확히 드러난다

→ 위에서 만든 useFetchProducts에 써보자

<figure><img src="../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

#### [useFetch](https://usehooks-ts.com/react-hook/use-fetch)

정말 간단히 쓸 때 좋음

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>빈 배열 error</p></figcaption></figure>

몇 가지 기능이 살짝 더 있는 useFetch 라이브러리가 따로 있다

* [use-http](https://use-http.com/#/)

조금 더 복잡해도 괜찮다면, 캐시 이슈를 고려한 좋은 대안이 있다

* [SWR](https://swr.vercel.app/ko): 혹시 data가 바뀌었는지를 확인해서 실시간으로 추가된걸 확인함
* [TanStack Query](https://tanstack.com/query/latest)(ex-React Query) &#x20;

#### [useInterval](https://usehooks-ts.com/react-hook/use-interval)

_**\* setInterval 사용시(상태등에 물릴시 문제가됨) 무조건 useInterval() 사용**_

React에서 setInterval 등을 쓸 때는 주의해야 할 부분이 있어서 Custom Hook을 만들어서 해결해야 함

* [useEffect 관점](https://overreacted.io/ko/a-complete-guide-to-useeffect/)
  * [React에서의 타이머 part 1 : setInterval 말고 이것! - 코드종님 영상](https://www.youtube.com/watch?v=2tUdyY5uBSw\&feature=youtu.be)
* _useEffect() 자급자족_

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

* [Ref 활용](https://overreacted.io/making-setinterval-declarative-with-react-hooks/)

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

#### [useEventListener](https://usehooks-ts.com/react-hook/use-event-listener)

모든 종류의 이벤트를 확인할 수 있음. 특히 dispatchEvent로 전달되는 커스텀 이벤트에 반응하기 좋다. (강력 추천!)

* useClickAnyWhere() - 아무대나 클릭하면 (클릭이벤트가  있으면 작동)
* 로그인 후 특히 외부랑 많이 물려있는 코드가 있을시, hook으로 빼기 싫고 아예 밖으로 빼고 싶을때, 어딘가 컴포넌트로 몰아주거나 할때 사용하면 굉장히 편함

14:30

[useLocalStorage](https://usehooks-ts.com/react-hook/use-local-storage)

localStorage와 JSON으로 객체 영속화

이벤트를 통해(dispatchEvent + useEventListener) 다른 컴포넌트와 동기화하는 게 매우 중요한 특징

[useDarkMode](https://usehooks-ts.com/react-hook/use-dark-mode)
