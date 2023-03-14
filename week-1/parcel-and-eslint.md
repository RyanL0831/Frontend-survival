# Parcel & ESLint

## 학습 키워드

* Bundler: Parcel (여러개의 파일들을 하나로 합쳐주는 tool)
* Lint: ESLint (code를 분석해서 도움을 주는 tool)

## Parcel

[**Parcel 공식문서**](https://parceljs.org/)

## Zero Configuration

* 설정 없이 바로 사용가능한 빌드 도구. SWC를 사용해 기존 도구보다 빠름
* 참고사이트:
  * [https://github.com/ahastudio/til/tree/main/parcel](https://github.com/ahastudio/til/tree/main/parcel)
  * [https://github.com/ahastudio/til/tree/main/vite](https://github.com/ahastudio/til/tree/main/vite)

## 추천 설정 2가지

* `package.json` 파일에 source 속성 추가.

```json
"source": "./index.html",
```

* parcel-reporter-static-files-copy 패키지 설치 후 `.parcelrc` 파일 작성.\
  이렇게 하면 static 폴더의 파일을 정적 파일로 Serving할 수 있다(이미지 등 Assets).

```json
{
  "extends": ["@parcel/config-default"],
  "reporters": ["...", "parcel-reporter-static-files-copy"]
}
```

## 빌드 + 정적 서버 실행

```bash
npx parcel build
npx servor ./dist
```

* [servor](https://github.com/lukejacksonn/servor)

## ESLint

* 린트 또는 린터
* ESLint가 TSLint를 흡수했다.
* 스스로의 rules 만들기.

[**ESLint 공식문서**](https://eslint.org/)

* [린트](https://ko.wikipedia.org/wiki/%EB%A6%B0%ED%8A%B8\_\(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4\))
* [정적 프로그램 분석](https://ko.wikipedia.org/wiki/%EC%A0%95%EC%A0%81\_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8\_%EB%B6%84%EC%84%9D)
* [Coding\_conventions](https://en.wikipedia.org/wiki/Coding\_conventions)
* 가독성을 위한 패턴 통일
* 잠재적 문제 발견
* best practice 추천

[VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

`.vscode/settings.json` 파일을 추가해 JS/TS 파일을 저장할 때마다 ESLint를 실행하고 문제점을 수정.

```json
{
  "editor.rulers": [80],
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "trailing-spaces.trimOnSave": true
}
```

아샬이 쓰는 VS Code 기본 세팅:

* [VS Code 기본 세팅](https://github.com/ahastudio/CodingLife/blob/main/20211008/react/.vscode/settings.json)
* [Trailing Spaces](https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces)
