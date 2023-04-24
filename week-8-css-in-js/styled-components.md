# styled-components

#### 학습 키워드

* styled-componets

> 💡 유명한 라이브러리들은 대부분 ‘왜’ 만들어졌는지 혹은 품고 있는 철학 등이 잘 정리되어 있는 경우가 많습니다. 라이브러리를 사용할 때는 공식문서를 꼭 살펴보는 습관을 하시는 게 좋습니다.
>
> 참고 레퍼런스:[https://styled-components.com/docs/basics](https://styled-components.com/docs/basics)

## styled-components

\|  [styled-components](https://styled-components.com/)

\|  [Babel Plugin](https://styled-components.com/docs/tooling#babel-plugin)

\|  [@swc/plugin-styled-components](https://github.com/swc-project/plugins/tree/main/packages/styled-components)

\|  [vscode-styled-components extention](https://marketplace.visualstudio.com/items?itemName=styled-components.vscode-styled-components)

스타일이 적용된 컴포넌트를 쉽게 만들 수 있는 도구

반드시 VS Code Extension을 설치해서 쓰자. 도구에서 제대로 지원 안 하면 사람이 쓸 게 못 됨

Babel Plugin을 SWC에서 쓸 수 있도록 포팅한 것도 함께 설치하자(SSR 지원 등을 위한 공식 권장사항)

```bash
npm i styled-components
npm i -D @types/styled-components @swc/plugin-styled-components
```

#### <mark style="color:red;">`.swcrc`</mark> 파일 작성

```typescript
{
	"jsc": {
		"experimental": {
			"plugins": [
				[
					"@swc/plugin-styled-components",
					{
						"displayName": true,
						"ssr": true
					}
				]
			]
		}
	}
}
```

#### 간단한 Styled Component 만들기

```typescript
import styled from 'styled-components';

const Paragraph = styled.p`
	color: #00F;
`;

export default function Greeting() {
	return (
		<Paragraph>
			Hello, world!
		</Paragraph>
	);
}
```

#### Styled Component에 추가로 스타일을 입히는 것도 가능하다

```typescript
import styled from 'styled-components';

const Paragraph = styled.p`
	color: #00F;
`;

const BigParagraph = styled(Paragraph)`
	font-size: 5rem;
`;

export default function Greeting() {
	return (
		<BigParagraph>
			Hello, world!
		</BigParagraph>
	);
}
```

#### 기존 컴포넌트에 스타일을 입히는 것도 가능. 단, 기존 컴포넌트가 Class를 잡아줘야 한다는 점에 주의!

```typescript
import styled from 'styled-components';

function HelloWorld({ className }: React.HTMLAttributes<HTMLElement>) {
	return (
		<p className={className}>
			Hello, world!
		</p>
	);
}

const Greeting = styled(HelloWorld)`
	color: #00F;
`;

export default Greeting;
```





