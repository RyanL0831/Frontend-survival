# Router

#### 학습 키워드

* ReactRouter - RouterProvider

## Router

React Router 버전 6.4부터 지원하는, 라우터 객체를 만들어서 쓰는 방법

* object 만들어 쓰는 개념과 유사함
* App()
  * 전체적으로 어떤 layout을 취하고 있는가
  * 어떻게 라우팅 되고 있는가
  * Layout 과 라우팅을 두개로 쪼개면 App()이 필요없어짐

라우팅 정보만 별도의 파일로 관리

```typescript
import { Outlet } from 'react-router-dom';

function Layout() {    //Layout 정의
  return (
    <div>
      <Header />
        <Outlet />     //react-router에서 지원
      <Footer />
    </div>
  );
}

// 라우팅 정보 잡기                              테스트에서도 route 정보가 필요
const routes = [
  {
     element: <Layout />,
     children: [                                    //객체가 두개니 따로
        { path: '/', element: <HomePage /> }, 
        { path: '/about', element: <AboutPage /> },
     ],
  },
];

export default routes;
```

#### App 컴포넌트를 거치지 않고 바로 브라우저 라우터 만들어서 사용

\|  [createBrowserRouter](https://reactrouter.com/en/main/routers/create-browser-router)

\|  [RouterProvider](https://reactrouter.com/en/main/routers/router-provider)

```typescript
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import routes from './routes';

const router = createBrowserRouter(routes);

root.render((
   <React.StrictMode>
      <RouterProvider router={router} />
   </React.StrictMode>
));
```

#### 메모리 라우터 만들어서 테스트

\|  [createMemoryRouter](https://reactrouter.com/en/main/routers/create-memory-router)

```typescript
describe('routes'', () => {	
  function renderRouter(path: string) {
    const router = createMemoryRouter(routes, { initialEntries: [path] });
    render(<RouterProvider router={router} />);
  }
	
context('when the current path is “/”', () => {
  it('renders the home page', () => {
    renderRouter('/');
	
    screen.getByText(/Hello/);
  });
});
	
context('when the current path is “/about”', () => {
    it('renders the about page', () => {
      renderRouter('/about');
	
      screen.getByText(/About/);
    });
  });
});
```











