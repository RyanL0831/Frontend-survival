# Routes

#### 학습 키워드

* 라우터란?
* React Router
  * Browser Router
  * Route
  * Memory Router

## React Router

\|  [React Router](https://reactrouter.com/en/main)

## Routes

\|  [Routes](https://reactrouter.com/en/main/components/routes)

\|  [Route](https://reactrouter.com/en/main/route/route)

#### 라우터 설치

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>실제로 나가야 하니 -d 안붙임</p></figcaption></figure>

#### Router - element, path

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>element 받음, path 받음</p></figcaption></figure>

#### 간단히 코드 옮기기

```typescript
import { Routes, Route } from 'react-router-dom';

function App() {
  return (
    <div>
      <Header />
      <main>
        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/about" element={<AboutPage />} />
        </Routes>
      </main>
      <Footer />
    </div>
  );
}
```

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>App에서 잡아줌</p></figcaption></figure>

#### 브라우저 라우터 내려주기

\|  [BrowserRouter](https://reactrouter.com/en/main/router-components/browser-router) - web browser 화면에서 씀. Main.tsx 에서 처리

```typescript
import { BrowserRouter } from 'react-router-dom';

root.render((
  <BrowserRouter>
    <App />
  </BrowserRouter>
));
```

#### 한 세트

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### \[테스트 환경]

#### 테스트 코드에선 메모리 라우터 사용

\|  [MemoryRouter](https://reactrouter.com/en/main/router-components/memory-router)

```typescript
import { MemoryRouter } from 'react-router-dom';

describe('App', () => {
  function renderApp(path: string) {
    render((
      <MemoryRouter initialEntries={[path]}>   //한 세트
        <App />                       //browser에서는 위치가 어디다 라는걸 URL로 알려주는데
      </MemoryRouter>   //memory에서는 위치가 없기에 initialEntries초기엔트리로 잡아줌(배열로)
    ));
  }
	
  context('when the current path is “/”', () => {
    it('renders the home page', () => {
      renderApp('/');                //경로가 '/' 면 homepage 그려줘

      screen.getByText(/Hello/);            //react testing library있는걸로 테스트
    });                            //머머가 잇는지 정확히 잡아 주기 위해서 getByText()
  });
	
  context('when the current path is “/about”', () => {
    it('renders the about page', () => {
      renderApp('/about');

      screen.getByText(/About/);    //test실패: about이 여러개 떠서
    });
  });
});
```











