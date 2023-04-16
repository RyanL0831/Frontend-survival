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

코드 레벨이 아니라 네트워크 레벨에서 가짜 구현. 오프라인 작업 등을 지원하기 위한 서비스 워커의 기능을 유용히 활용한 것.

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

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));

afterAll(() => server.close());

afterEach(() => server.resetHandlers());
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

```javascript
import { rest } from 'msw';

const BASE_URL = 'http://localhost:3000';

const handlers = [
	rest.get(`${BASE_URL}/products`, (req, res, ctx) => {
		const products = [
			{
				category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
			},
		];

		return res(
			ctx.status(200),
			ctx.json({ products }),
			);
		}),
	];

export default handlers;
```

#### <mark style="color:red;">App.test.ts</mark> 파일

```javascript
import { render, screen, waitFor } from '@testing-library/react';

import App from './App';

// jest.mock 불필요.

test('App', async () => {
	render(<App />);
	
	await waitFor(() => {
		screen.getByText('Apple');
	});
});
```

#### 너무 본격적으로 코딩하면 사실상 백엔드를 개발하게 되니, 이 부분에 주의할 것

테스트 환경(Node.js 기반) 외에 웹 브라우저도 지원하기 때문에, API 스펙은 나왔지만 아직 구현되지 않은 경우 임시로 사용할 수도 있다. 단순히 임시 서버를 만들 거라면 Express를 쓰는 게 더 낫지만, 테스트 코드도 지원하면서 겸사겸사 웹 브라우저를 지원하는 용도로는 나쁘지 않은 선택이다.

* [GitHub에서 만든 fetch polyfill](https://github.com/github/fetch)











