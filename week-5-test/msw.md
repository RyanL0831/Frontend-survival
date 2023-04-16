# MSW

#### 학습 키워드

* Service worker
* MSW(Mock Service Worker)
* polyfill(폴리필)

## MSW (Mock Service Worker)

\| [MSW](https://mswjs.io/)

|[ Service Worker API](https://developer.mozilla.org/ko/docs/Web/API/Service\_Worker\_API)

\| [아샬의 Mock Service Worker (MSW)](https://github.com/ahastudio/til/blob/main/mock-api/msw.md)

|[ Mocking REST API](https://mswjs.io/docs/getting-started/mocks/rest-api)

\| [Integrate mocking into Node](https://mswjs.io/docs/getting-started/integrate/node)

코드 레벨이 아니라 네트워크 레벨에서 가짜 구현. 오프라인 작업 등을 지원하기 위한 서비스 워커의 기능을 유용히 활용한 것

* Node 에서 사용가능
* 브라우저에서 사용가능
* 네트워크 lvl에서 프록시를 활용하여 사용됨

#### MSW 패키지 설치

```bash
npm i -D msw
```

#### <mark style="color:red;">jest.config.js</mark> 파일의 “setupFilesAfterEnv” 속성에 <mark style="color:red;">setupTests.ts</mark> 파일 추가

```javascript
module.exports = {
	testEnvironment: 'jsdom',
	setupFilesAfterEnv: [
		'@testing-library/jest-dom/extend-expect',
		'<rootDir>/src/setupTests.ts',
	],
	transform: {
		'^.+\\.(t|j)sx?$': ['@swc/jest', {
			jsc: {
				parser: {
					syntax: 'typescript',
					jsx: true,
					decorators: true,
				},
				transform: {
					react: {
						runtime: 'automatic',
					},
				},
			},
		}],
	},
};
```

#### <mark style="color:red;">src/setupTests.ts</mark> 파일

```javascript
import server from './mocks/server';

beforeEach() //test 하나하나 실행할때마다 먼저 실행되는것

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));
//jest 실행 할때 바로 되는것         handler 안잡았을때 error 출력처리

afterAll(() => server.close()); //전부 끝날때

afterEach(() => server.resetHandlers()); //각각 테스트 끝날때마다
```

#### <mark style="color:red;">src/mocks/server.ts</mark> 파일

```javascript
import { setupServer } from 'msw/node';

import handlers from './handlers';

const server = setupServer(...handlers);

export default server;
```

#### <mark style="color:red;">src/mocks/handlers.ts</mark> 파일

&#x20;  → Express의 경험을 살려보자!

<pre class="language-javascript"><code class="lang-javascript">import { rest } from 'msw';

const BASE_URL = 'http://localhost:3000' || process.env.API_BASE_URL; //환경변수로 잡아줌

const <a data-footnote-ref href="#user-content-fn-1">handlers </a>= [
	rest.get(`${BASE_URL}/products`, (req, res, ctx) => {
	                    //req: request, res: response, ctx: context
  //  option 1: const products = fixtures.products
  //         -> const { products } = fixtures;
  //                 or  below	
		const products = [
			{
				category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
			},
		];
//              option1 으로 했을때 
//         ->   return { products };
		return res(
			ctx.status(200), // 생략가능(기본이 200임)
			ctx.json({ products }),
			);
		}),
	];

export default handlers;
</code></pre>

#### <mark style="color:red;">App.test.ts</mark> 파일

```javascript
import { render, screen, waitFor } from '@testing-library/react';

import App from './App';

// jest.mock 불필요.

test('App', async () => {
	render(<App />);
// rendering 한다음에 바로 찾으려면 못찾음. 여기 걸릴때까지 기다려주는게 필요	
	await waitFor(() => {  // function 내용이 될때까지 확인한다 or 기다린다
		screen.getByText('Apple');
	});
});
```

#### 너무 본격적으로 코딩하면 사실상 백엔드를 개발하게 되니, 이 부분에 주의할 것

테스트 환경(Node.js 기반) 외에 웹 브라우저도 지원하기 때문에, API 스펙은 나왔지만 아직 구현되지 않은 경우 임시로 사용할 수도 있다. 단순히 임시 서버를 만들 거라면 Express를 쓰는 게 더 낫지만, 테스트 코드도 지원하면서 겸사겸사 웹 브라우저를 지원하는 용도로는 나쁘지 않은 선택이다.

* [GitHub에서 만든 fetch polyfill](https://github.com/github/fetch)













[^1]: 
