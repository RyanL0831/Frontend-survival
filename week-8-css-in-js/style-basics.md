# Style Basics

#### 학습 키워드

* className
* 의미있는 마크업

> 💡 의미있는 마크업을 하기 위해서는 HTML Element 들이 어떤 의미를 가지고 있는지 정확하게 알고 있어야 합니다. 레퍼런스를 참고하여 HTML 마크업에 대해 정확하게 이해한 뒤 정리하고 넘어가시면 좋습니다.
>
> 참고 레퍼런스:[https://developer.mozilla.org/ko/docs/Web/HTML/Reference](https://developer.mozilla.org/ko/docs/Web/HTML/Reference)

## parcel-cache 초기화

\* 기존의 소스가 충돌할때 terminal 에서 소스 초기화                                                                                 (새로  짤때는 관련 없음,  기존을재활용 할때 같은 폴더일 경우 문제가  됨)&#x20;

```bash
$ rm -rf .parcel-cache
$ rm -rf dist
```

## Basic: Class

\|  [Basic: Class](https://ko.legacy.reactjs.org/docs/faq-styling.html)

`index.html` 파일에 간단히 CSS 추가.

```typescript
<style>
	.greeting {
		color: #00F;
	}
</style>
```

#### “className” 지정. ( JS에서  class랑   곂쳐서 className)&#x20;

```typescript
export default function Greeting() {
	return (
		<p className="greeting">
			Hello, world!
		</p>
	);
}
```

CSS는 컴포넌트를 전제로 하고 있지 않음. 공통된 부분이 많을 때 재사용하기 쉽다.

따라서, 컴포넌트 중심으로 빠르게 작업하려고 하면 불편할 때가 많다. 재사용은 그냥 컴포넌트를 사용하면 된다.

절충안으로 아주 작은 스타일 그룹을 클래스로 지정하는 방법도 있긴 하다(Bootstrap, Tailwind CSS 등의 접근법).

## ID 찾을때

* 1개 일때 or 제일 처음 것

```typescript
document.querySelector('.greeting')
```

* 다수 일때

```typescript
document.querySelectorAll('.greeting')
```

#### ID는 고유 / class는 그룹

## Basic: Inline Style

\* CSS는 아님, JavaScript 안에서

“style” 속성 활용. 평범한 JavaScript 객체를 활용하므로 변수, 함수 등을 재사용하기 쉽다. 텍스트가 아니라서 실수하거나 불편할 때가 있다. TypeScript의 힘으로 자동완성, 타입 검사 등의 도움을 받을 수 있다.

```typescript
export default function Greeting() {
	const style = {
		color: '#00F',         //객체화
	};
	
	return (
		<p style={style}>
			Hello, world!
		</p>
	);
}
```

바로 쓸 수도 있음

```typescript
export default function Greeting() {
	return (                                //객체를 그대로 넣어줌
		<p
		   style={{
		      color: '#00F',
		   }}
		>
			Hello, world!
		</p>
	);
}
```

#### darkMode 예시)

```typescript
const darkMode = false;

function primaryColor() {
  if (darkMode) {
    return 'F00'
  }
  return '#00F'
  
  // or
  
  return darkMode ? '#F00' : '#00F';

}

export default function Greeting() {
  return (
    <p
      style={{
        color: primaryColor,
      }}
    >
      Hello, world!
    </p>
  )
}
```
