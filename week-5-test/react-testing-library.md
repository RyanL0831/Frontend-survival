# React Testing Library

#### 학습 키워드

* React Testing Library
* given - when - then 패턴
* Mocking
* Test fixture

## React Testing Library

\| [React Testing Library](https://github.com/testing-library/react-testing-library)

\| [jest-dom](https://github.com/testing-library/jest-dom)

#### !![](<../.gitbook/assets/image (1) (2).png>)<mark style="background-color:blue;">React 컴포넌트를 사용자 입장에 가깝게 테스트할 수 있는 도구</mark>

```javascript
import { render, screen } from '@testing-library/react';

import TextField from './TextField';

test('TextField', () => {	
	const text = 'Tester';
	const setText = () => {
		// do nothing...
	};

	render((	
		<TextField
			label="Name"
			placeholder="Input your name"
			text={text}
			setText={setText}		
		/>
	));
	
	screen.getByLabelText('Name');
});
```

테스트 코드, 즉 컴포넌트를 사용하는 코드를 작성하면서 해당 컴포넌트의 인터페이스를 점검할 수 있다. 기존에는 label이 빠져있었고, text 같이 범용적인 표현을 사용하지 않은 문제가 있었다. 개발하면서 이런 문제를 발견할 수도 있지만, 우리가 테스트부터 작성했거나 빠르게 테스트 코드를 작성했다면 작성하기 전 또는 바로 직후에 문제를 발견해서 수정할 수 있었을 것. 시간이 지나면 해당 코드에 대한 지식이 감소하고, 자신감 또한 감소하기 때문에 건드리기 힘든 코드가 되기 십상이다

#### BDD 스타일로 코드를 바꾸고, 입력 등이 잘 작동하는지 확인해 보자

```javascript
import { render, screen, fireEvent } from '@testing-library/react';

import TextField from './TextField';

const context = describe;

describe('TextField', () => {
	const text = 'Tester';
	const setText = jest.fn();
	
	beforeEach(() => {
		setText.mockClear();
		// 또는 jest.clearAllMocks();	
	});
	
	function renderTextField() {
		render((
			<TextField
				label="Name"
				placeholder="Input your name"
				text={text}
				setText={setText}
			/>
		));
	}
	
	it('renders an input control', () => {
		renderTextField();

		screen.getByLabelText('Name');
	});
	
	context('when user types text', () => {	
		it('calls the change handler', () => {
			renderTextField();

			fireEvent.change(screen.getByLabelText('Name'), {
				target: {
					value: 'New Name',
				},
			});
	
			expect(setText).toBeCalledWith('New Name');
		});
	});
});ja
```

반복되는 코드를 Extract Function하고, fireEvent 등을 통해 인터랙션만 검증한다. 만약 복잡한 로직이 컴포넌트로부터 분리된다면, 여기서는 이것만 검증하면 된다.

#### 만약 외부 의존성이 큰 코드를 작성한다면, 해당 부분만 가짜로 구현할 수 있다.

```javascript
import { render, screen } from '@testing-library/react';

import App from './App';

jest.mock('./hooks/useFetchProducts', () => () => [
	{
		category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
	},
]);

test('App', () => {
	render(<App />);

	screen.getByText('Apple');
});
```

일반적으론 백엔드와 소통하는 부분이 차지하는 비중이 큰데, 이 부분을 하나씩 가짜 구현으로 바꾸다 보면 어려울 때가 있다. 이럴 땐 MSW 등 다른 대안을 고려해 보자.

