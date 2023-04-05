# Express

## 학습 키워드

* Express 란
* URL 구조
* REST API
* HTTP Method (CRUD)

## Express

> [Express ](https://expressjs.com/ko/)

\- node JS 초창기 web framework

\- 아폴로 server + express 조합

## 간단한 서버 앱 npm 패키지 세팅

> [Express 설치](https://expressjs.com/ko/starter/installing.html)

> [ts-node](https://github.com/TypeStrong/ts-node)

\- node 무조건 npm

```bash
mkdir express-demo-app
cd mkdir express-demo-app
```

#### 잊지 말고 .gitignore 파일 준비!

```bash
touch .gitignore          // 만들어줌
echo "/node_modules/"      // 화면에 보여줌
echo "/node_modules/" > .gitignore     //gitignore에 추가됨

```

#### 패키지 초기화

```bash
npm init -y
```

<figure><img src="../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

#### TypeScript

```bash
npm i -D typescript   // npm i --save-dev typescript 와 같음 (devDependencies로 들어감)
npx tsc --init        // TS config 파일을 만들어줌
```

<figure><img src="../.gitbook/assets/image (13) (1).png" alt=""><figcaption><p>npm i -D typescript</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10) (1).png" alt=""><figcaption><p>npx tsc --init</p></figcaption></figure>

## \* 00:05:33 \*&#x20;

#### ts-node 설치

```bash
npm i -D ts-node
```

####

#### ESLint

```bash
npm i -D eslint
npx eslint --init
```



#### Express 설치

```bash
npm i express
npm i -D @types/express
```



#### Hello World 예제

[Express 예제](https://expressjs.com/ko/starter/hello-world.html)



#### TypeScript에 맞춰서 app.ts 파일 작성.

```javascript
import express from 'express';

const port = 3000;

const app = express();

app.get('/', (req, res) => {
	res.send('Hello, world!');
});

app.listen(port, () => {
	console.log(`Server running at http://localhost:${port}`);
});
```



#### ts-node로 실행.

```bash
npx ts-node app.ts
```



#### 코드를 수정할 때마다 서버를 재실행해야 하는 문제를 피하기 위해 [nodemon](https://github.com/remy/nodemon) 사용.

```bash
npm i -D nodemon
npx nodemon app.ts
```



## REST API

Roy Fielding - “[Architectural Styles and the Design of Network-based Software Architectures](https://www.ics.uci.edu/\~fielding/pubs/dissertation/top.htm)” (2000)

[Richardson Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html)



#### 대개는 “필딩 제약 조건” 4가지를 모두 만족하지 않고, Resource와 HTTP Verb만 도입하는 수준으로 사용.

* 이렇게 안 하고: /write-post
* 이렇게 하자: /posts → 뭔가를 한다 (CRUD)



#### CRUD에 대해 HTTP Method를 대입. Read는 Collection(복수)과 Item(Element)(단수)로 나뉨.



#### 기본 리소스 URL: /products

1. Read (Collection) → GET /products ⇒ 상품 목록 확인
2. Read (Item) → GET /products/{id} ⇒ 특정 상품 정보 확인
3. Create (Collection Pattern 활용) →  PUT or POST /products ⇒ 상품 추가 (JSON 정보 함께 전달)
4. Update (Item) → PUT 또는 PATCH /products/{id} ⇒ 특정 상품 정보 변경 (JSON 정보 함께 전달)
5. Delete (Item) → DELETE /products/{id} ⇒ 특정 상품 삭제

_\* PUT은 없으면 만들어주고, 있으면 덮어 씌움 (PATCH 일부만 변경, 최근 생김)_

#### Thinking in React 예제

```javascript
app.get('/products', (req, res) => {

	const products = [
		{
			category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
		},
		{
			category: 'Fruits', price: '$1', stocked: true, name: 'Dragonfruit',
		},
		{
			category: 'Fruits', price: '$2', stocked: false, name: 'Passionfruit',
		},
		{
			category: 'Vegetables', price: '$2', stocked: true, name: 'Spinach',
		},
		{
			category: 'Vegetables', price: '$4', stocked: false, name: 'Pumpkin',
		},
		{
			category: 'Vegetables', price: '$1', stocked: true, name: 'Peas',
		},
	];
	
	res.send({ products }); //자동으로 JSON으로 변환. JSON.stringify() 안써야 더 전달이 잘됨
	res.send( products );  //이렇게도 표현 가능
	res.send({ products, pages: { currentPage: 1, totalPages: 10 } }); //이렇게도 구분함 
});
```

#### localhost:3000 에서 확인

<figure><img src="../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

#### TERMINAL에서 Curl 으로 확인 가능

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

#### TERMINAL에서 HTTP 으로 확인 가능

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>
