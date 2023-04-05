# React의 Hook

## 학습 키워드

* React Hooks 이란
* Hooks
  * useState
  * useEffect
  * useContext
  * useRef
  * useLayoutEffect
* React StrictMode 란

#### React의 Hooks

* [Hooks ](https://ko.reactjs.org/docs/hooks-intro.html)소개
* [Hooks 개요](https://ko.reactjs.org/docs/hooks-overview.html)
* [Hooks API Reference](https://ko.reactjs.org/docs/hooks-reference.html)

React 16.8에서 Hooks가 도입됨. 기존 방식에 있던 몇 가지 문제를 해결

[React Conf 2018 Hooks 소개 영상](https://www.youtube.com/watch?v=dpw9EHDh2bM)

#### 기존 방식의 문제점:

* Wrapper Hell (HoC)
  * HoC가 상태를 관리하게 만듬
* Huge Components 컴포넌트가 커지는 문제점&#x20;
* Confusing Classes (참조 [You Don't Know JS Yet](https://github.com/getify/You-Dont-Know-JS))
  * class는 객체지향과 무관함
  * Function Component -> Hooks 로 모든걸 처리 가능함

[HoC (Higher-Order Components)](https://ko.reactjs.org/docs/higher-order-components.html) 고차 컴포넌트

* 재활용에 많이 씀

React를 쓰는 방식을 완전히 바꾼 커다란 변화

&#x20;  \-> 이제는 예전으로 돌아가는게 불가능하다! (예전엔  상태를 가진 components를 class components로 만듬)

#### 기존:

* 상태를 가진 컴포넌트는 Class Component로 만들고, props만 사용하는 재사용이 용이한 작은 컴포넌트는 Function Component로 작성
* Redux에서도 비슷한 구분이 존재했다
  * [Presentational and Container Components - Dan Abramov](https://medium.com/@dan\_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
    * Presentational Components - Props만 사용. Props가 같으면 결과물이 같음
    * Container Components - 상태를 가짐. Redux와 연결이됨

#### 현재:

* 그냥 Function Component만 (Hooks으로) 사용
* 상태 관리 유무를 바로 알기 어려움 = 신경쓰지 않아도 됨
* 복잡한 요소는 전부 Hook으로 격리 및 재사용 가능

#### 대표적인 Hooks

* 기본1  useState -> State Hook => React의 State
* 기본2 useEffect => Side-effect
* 기본3 useContext
* useRef
* useLayoutEffect -> useEffect와 조금 (실행타이밍)다름

## useEffect

\| [Synchronizing with Effects](https://react.dev/learn/synchronizing-with-effects)

* 외부와 synchronize를 함 (effect 존재 이유)

\| [You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect)

\| [Using the Effect Hook](https://ko.reactjs.org/docs/hooks-effect.html)

\| [useEffect](https://react.dev/reference/react/useEffect)

\| [useEffect 완벽 가이드](https://overreacted.io/ko/a-complete-guide-to-useeffect/)

_**렌더링 이후 해야 할 일(화면에 그리는것만 하진 않음)**_, 즉 React의 외부와 관련된 일을 정해줄 수 있다

기본적으로 렌더링 때마다 실행되므로, 의존성 배열을 통해 언제 이펙트를 실행할지 지정할 수 있다(= 불필요한 경우에 건너뛸 수 있다)

**함수를 리턴함으로써 종료 처리**를 할 수 있다

### 타이머의 예제

React의 외부에 우아하게 접근. 이정도는 useEffect를 안 쓴다고 크게 문제가 되지 않지만, 이렇게 쓰는 습관을 들이자

```javascript
document.title = 'XXX'; //이렇게 할수 있지만 좀더 우와하게 밑에 방식
                        //Server side 랜더링 등 여러가지 요소 고려
useEffect(() => {       //effect가 있을때 마다 활성화됨
	document.title = `Now: ${new Date().getTime()}`; //새로고침 때마다 시간업데이트
});
```

타이머를 on/off하는 기능을 그냥 만들면 문제가 발생한다

```javascript
//timer를 0.1초씩마다 갱신하는 effect
useEffect(()=>{
  console.log('Effect');
  setInterval(()=>{
    document.title = `Now: ${new Date().getTime()}`;
  }, 100);
})

function Timer() {
	useEffect(() => {
		setInterval(() => {
			document.title = `Now: ${new Date().getTime()}`;
		}, 100);
	});

	return (
		<p>Playing</p>
	);
}

export default function TimerControl() {
	const [playing, setPlaying] = useState(false);
	
	const handleClick = () => {
		setPlaying(!playing); //on -> off, off -> on
	};

	return (
		<div>
			{playing ? (
				<Timer />
			) : (
				<p>Stop</p>
			)}
			<button type="button" onClick={handleClick}>
				Toggle
			</button>
		</div>
	);
}
```

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>setInterval() 이 계속돔 (시간이 사라지않음)</p></figcaption></figure>

## \* 18:54 \*

#### 종료 처리

```javascript
useEffect(() => {
	const savedTitle = document.title;

	const id = setInterval(() => {
		document.title = `Now: ${new Date().getTime()}`;
	}, 100);

	return () => {
		document.title = savedTitle;
		clearInterval(id);
	};
});
```

#### 처음에 한번만 실행하기

의존성 배열에서 아무 것도 지정하지 않으면 맨 처음에 딱 한번만 실행하게 할 수 있다

주로 API를 호출해서 데이터를 얻을 때 사용한다

```javascript
const [products, setProducts] = useState<Product[]>([]);

useEffect(() => {
	const fetchProducts = async () => {
		const url = 'http://localhost:3000/products';
		const response = await fetch(url);
		const data = await response.json();
		setProducts(data.products);
	};

	fetchProducts();
}, []);
```

Fetch 함수의 위치가 고민된다면, Dan Abramov의 글을 다시 보자

[useEffect 완벽가이드 - 함수를 이펙트 안으로 옮기기](https://overreacted.io/ko/a-complete-guide-to-useeffect/#%ED%95%A8%EC%88%98%EB%A5%BC-%EC%9D%B4%ED%8E%99%ED%8A%B8-%EC%95%88%EC%9C%BC%EB%A1%9C-%EC%98%AE%EA%B8%B0%EA%B8%B0)

#### Effect가 두 번 실행되는 문제

\<React.StrictMode>로 컴포넌트 전체를 감쌀 경우, 예상치 못한 Side Effect를 찾으려고 Effect 등을 두 번씩 실행함. 평소에는 큰 문제가 없지만, API 등을 사용하면 이상하다고 느낄 수 있으니 참고할 것

[예상치 못한 부작용 검사](https://ko.reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)

#### 의존성 배열을 이용해 Fetch할 때 주의사항

[Fetching data](https://beta.reactjs.org/learn/synchronizing-with-effects#fetching-data)



