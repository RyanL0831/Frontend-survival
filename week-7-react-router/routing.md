# Routing

#### 학습 키워드

* HTML DOM API
  * Location
  * pathname

## Routing

\|  [Window.location](https://developer.mozilla.org/ko/docs/Web/API/Window/location)

\|  [Location](https://developer.mozilla.org/ko/docs/Web/API/Location)

일반적인 웹 사이트는 URL에 따라 다른 웹 페이지를 보여준다. 하나의 웹 페이지를 하나의 컴포넌트로 만들고, URL에 따라 적절한 컴포넌트가 보이게 함으로써 구현 가능함

#### location.hash 예제)

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

#### .hash: encoding URI <=> decoding URI

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### location.host vs location.hostname

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

#### pages/HomePage.tsx

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### pages/AboutPage.tsx

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

#### components/Header.tsx

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

```typescript
import Header from './components/Header';
import footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

function App() {
  const { pathname } = window.location; //window가 global이므로 .location과 같음
					//path에 따른 각각 다른 처리
  return (
    <div>        //<p> tag는 error 발생
      <Header />       //components로 빼줌
        <main>
          {pathname === '/' && <HomePage />}
          {pathname === '/about' && <AboutPage />}
        </main>
      <Footer />
    </div>
  );
}
```

<pre class="language-typescript"><code class="lang-typescript"><strong>//const pages: Record&#x3C;string, React.FC> = {   //FC = function componenets
</strong>                                              //"어떤 parameter 들어갑니다" 잡아줄수 있음
                                              //없으면 기본!
const pages = {
  '/': HomePage,
  '/about': AboutPage,
};

function App() {
  const { pathname } = window.location; 
					
  const Page = Reflect.get(pages, path) || HomePage;   //주는 대로 받는

  return (
    &#x3C;div>        
      &#x3C;Header />       
        &#x3C;main>
          &#x3C;Page />
        &#x3C;/main>
      &#x3C;Footer />
    &#x3C;/div>
  );
}
</code></pre>

## Test

#### App.test.tsx

```typescript
import { render } from '@testing-library/react';

import App from './App';

test('App', () => {
  //window               * window가 임의로는 있지만, 진짜로 있지는 않음
  //const path = window.location.pathname; 을 추상화하여 테스트할수 있지만 직접하진않고,
  render(<App />);       //                                     React Router를 사용
});
```
