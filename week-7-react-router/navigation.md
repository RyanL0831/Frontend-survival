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

```typescript
function Header() {

return (
	<header>
		<nav>
			<ul>
				<li><Link to="/">Home</Link></li>
				<li><Link to="/about">About</Link></li>
			</ul>
		</nav>
	</header>
	);
}
```

### NavLink

\|  [NavLink](https://reactrouter.com/en/main/components/nav-link)

```typescript
function Header() {
	return (
		<header>
			<nav>
				<ul>
					<li><NavLink to="/">Home</NavLink></li>
					<li><NavLink to="/about">About</NavLink></li>
				</ul>
			</nav>
		</header>
	);
}
```

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

```typescript
import { useNavigate } from 'react-router-dom';

export default function Footer() {
	const navigate = useNavigate();
	
	const handleClick = () => {
		navigate('/about');
	};
	
	return (
		<footer>
			<button type="button" onClick={handleClick}>
				Press
			</button>
		</footer>
	);
}
```












