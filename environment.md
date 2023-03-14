# 학습 키워드

- Node.js
- NPM(Node Package Manager)
  - package.json / package-lock.json
  - node_modules
  - npx
- ES Modules vs CommonJS

### TypeScript + React + Jest + ESLint + Parcel(번들러, 빌드 도구, 만능 도구) 개발 환경 세팅

작업 폴더 준비

- mkdir my-all
- cd my-app

편집기(VSCode) 열기

- code .
- webstorm . (웹스톰)

npm 패키지 준비

- npm init
- npm init -y (한번에 package.json 생성)
- name은 kebab-case, Lisp-case
- version은 semantic versioning
  - major.minor.patch

.gitignore 세팅

- touch .gitignore
- node_modules/
- dist/
- github/gitignore 혹은 vscode에서 .gitignore을 생성하면 편리

타입스크립트 설정

- npm i -D typescript
  - -D 옵션은 package.json의 devDependencies에 설치된다.
  - 개발 환경에서만 사용되는 툴
  - 과거에는 npm i --save-dev
- npx tsc --init
  - node_modules/.bin/tsc --init 명령어와 같다.
  - npx는 node_modules에 해당하는 패키지가 설치되어 있으면 찾아서 실행하고, 만약 설치되어 있지 않더라도 npm 패키지들을 캐시하는 곳에 다운로드를 받아서 설치하지 않아도 사용할 수 있도록 해준다.
    - macOS의 경우에 ~/.npm/\_npx 에 존재한다.
  - "jsx" : "react-jsx" 설정을 맞춰준다.
    - .tsx 파일을 사용하게 해준다.
    - import React를 하지 않아도 사용할 수 있게 해준다.

ESLint 설정

- npm i -D eslint
- npx eslint --init
- env에 jest:true를 미리 잡아줄 것.
- .eslintignore 작성

리액트 설치

- npm i react react-dom
- npm i -D @types/react @types/react-dom

테스팅 도구 설치

- npm i -D jest @types/jest @swc/core @swc/jest \
   jest-environment-jsdom \
   @testing-library/react @testing-library/jest-dom

jest.config.js 설정

- 성능을 위해 테스트에서 SWC를 사용할 수 있도록 세팅

Parcel 설치

- npm i -D parcel
- package.json scripts 수정

---

## 만들어진 개발 환경 (React)

- CRA (Create-React-App)
  - npx create-react-app my-app --template typescript
- Vite
  - yarn create vite
- CNA (Create-Next-App)
  - npx create-next-app@latest

CRA는 이제 자리에서 물러나고 Vite가 자리를 차지한 것 같다.  
개발 환경에서의 HMR(Hot Module Reloading), build 속도가 매우 빠르다. 번들이 없는 개발 서버다.