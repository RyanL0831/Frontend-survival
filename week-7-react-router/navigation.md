# Navigation

#### 학습 키워드

* Web APIs - History
* React Router - NavLink, Link, Navigate, useNavigate

## Navigation

### History.pushState

\|  [History.pushState()](https://developer.mozilla.org/ko/docs/Web/API/History/pushState)

```typescript
const state = {};
const title = '';
const url = '/about';

history.pushState(state, title, url);
```

### Link

\|  [Link](https://reactrouter.com/en/main/components/link)

<pre class="language-typescript"><code class="lang-typescript">function Header() {

return (
   &#x3C;header>
      &#x3C;nav>
         &#x3C;ul>
            &#x3C;li>&#x3C;Link to="/">Home&#x3C;/Link>&#x3C;/li>
            &#x3C;li>&#x3C;Link to="/about">About&#x3C;/Link>&#x3C;/li>
            &#x3C;li>&#x3C;Link to="/" className={example ? 'active' : ''}>Test&#x3C;/Link>&#x3C;/li>
         &#x3C;/ul>                      //NavLink의 수동 버전 
      &#x3C;/nav>
<strong>   &#x3C;/header>
</strong>   );
}
</code></pre>

### NavLink

\|  [NavLink](https://reactrouter.com/en/main/components/nav-link)

<pre class="language-typescript"><code class="lang-typescript">function Header() {
   return (
      &#x3C;header>
<strong>         &#x3C;nav>
</strong>            &#x3C;ul>
               &#x3C;li>&#x3C;NavLink to="/">Home&#x3C;/NavLink>&#x3C;/li>
               &#x3C;li>&#x3C;NavLink to="/about">About&#x3C;/NavLink>&#x3C;/li>
            &#x3C;/ul>
         &#x3C;/nav>
<strong>      &#x3C;/header>
</strong>   );
}
</code></pre>

class .active 로 현재 pg 주소를 잡아줌

### Navigate

\|  [Navigate](https://reactrouter.com/en/main/components/navigate)

```typescript
import { Navigate } from 'react-router-dom';

export default function LoginPage() {
   return (
      <Navigate to="/" />
   );
}
```

#### 테스트에서 “ReferenceError: Request is not defined” 에러가 나면 “whatwg-fetch”를 임포트해서 해결할 수 있다

### useNavigate

\|  [useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

<pre class="language-typescript"><code class="lang-typescript">import { useNavigate } from 'react-router-dom';

export default function Footer() {
   const navigate = useNavigate();
	
<strong>   const handleClick = () => {
</strong>      navigate('/about');
   };
	
   return (
<strong>      &#x3C;footer>
</strong>         &#x3C;button type="button" onClick={handleClick}>
            Press
         &#x3C;/button>
<strong>      &#x3C;/footer>
</strong>   );
}
</code></pre>













