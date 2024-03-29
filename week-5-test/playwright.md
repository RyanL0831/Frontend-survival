# Playwright

#### 학습 키워드

* E2E(End to End) Test
* Headless Chrome
* Puppeteer
* Playwright
* CodeceptJS

## Playwright

\| [Playwright](https://playwright.dev/)

\| [Playwright Configuration](https://playwright.dev/docs/test-configuration)

\| [Ashal의 Playwright](https://github.com/ahastudio/til/blob/main/test/playwright.md)

#### ! <mark style="background-color:blue;">웹 브라우저 기반 E2E 테스트 자동화 도구. Headless Chrome을 기반으로 한 Puppeteer(구글에서 만듬)를 계승하면서, 더 많은 웹 브라우저를 지원한다</mark>

* Headless browser (가볍게) - 화면에 안뜸, 뒤에서만 돌아감
* Phantom JS - 크롬기반, 크롬이 어떻게 돌아가는지

#### Playwright 패키지 설치

```bash
npm i -D @playwright/test eslint-plugin-playwright
```

#### <mark style="color:red;">playwright.config.ts</mark> 파일

```javascript
import { PlaywrightTestConfig } from '@playwright/test';

const config: PlaywrightTestConfig = {
	testDir: './tests',
	retries: 0,
	use: {
		baseURL: 'http://localhost:8080',
		headless: !!process.env.CI,
		screenshot: 'only-on-failure',
	},
};

export default config;
```

#### <mark style="color:red;">tests/.eslintrc.js</mark> 파일

```javascript
module.exports = {
	env: {
		jest: false,
	},
	extends: ['plugin:playwright/playwright-test'],
	rules: {
		'import/no-extraneous-dependencies': 'off',
	},
};
```

#### <mark style="color:red;">tests/home.spec.ts</mark>

```javascript
import { test, expect } from '@playwright/test';

test('Filter products', async ({ page }) => {
	await page.goto('/');

	await expect(page.getByText('Apple')).toBeVisible();

	const searchInput = page.getByLabel('Search');

	await searchInput.fill('a');

	await expect(page.getByText('Apple')).toBeVisible();

	await searchInput.fill('aa');

	await expect(page.getByText('Apple')).toBeHidden();
});

test('Click the “Increase” button', async ({ page }) => {
	await page.goto('/');

	const count = 13;

	await Promise.all((
		[...Array(count)].map(async () => {
			await page.getByText('Increase').click();
		})
	));

	await expect(page.getByText(`${count}`)).toBeVisible();
});
```

#### 테스트 실행

```bash
npx playwright test
```

#### <mark style="color:red;">`.gitignore`</mark> 파일에 에러 상황의 스크린샷 등이 담기는 <mark style="color:red;">`test-results`</mark> 디렉터리 추가

```
/test-results/
```

#### 인간 친화적인 E2E 테스팅 도구로 CodeceptJS가 있다

* [CodeceptJS](https://codecept.io/)
* [CodeceptJS 3 시작하기](https://github.com/ahastudio/til/blob/main/test/20201207-codeceptjs.md)
* [CodeceptJS 사용](https://github.com/ahastudio/CodingLife/tree/main/20211012/react#codeceptjs-%EC%82%AC%EC%9A%A9)







