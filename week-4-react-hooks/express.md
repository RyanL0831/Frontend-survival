# Express

## 학습 키워드

* Express 란
* URL 구조
* REST API
* HTTP Method (CRUD)

## Express

> [Express ](https://expressjs.com/ko/)



## 간단한 서버 앱 npm 패키지 세팅

> [Express 설치](https://expressjs.com/ko/starter/installing.html)

> [ts-node](https://github.com/TypeStrong/ts-node)



```bash
mkdir express-demo-app
cd mkdir express-demo-app
```



#### 잊지 말고 .gitignore 파일 준비!

```bash
touch .gitignore
echo "/node_modules/" > .gitignore
```



#### 패키지 초기화

```bash
npm init -y
```



#### TypeScript

```bash
npm i -D typescript
npx tsc --init
```



#### ESLint

```bash
npm i -D eslint
npx eslint --init
```



#### ts-node 설치

```bash
npm i -D ts-node
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
3. Create (Collection Pattern 활용) → POST /products ⇒ 상품 추가 (JSON 정보 함께 전달)
4. Update (Item) → PUT 또는 PATCH /products/{id} ⇒ 특정 상품 정보 변경 (JSON 정보 함께 전달)
5. Delete (Item) → DELETE /products/{id} ⇒ 특정 상품 삭제



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
	
	res.send({ products });
});
```













