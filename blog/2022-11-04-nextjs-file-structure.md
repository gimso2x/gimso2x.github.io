---
slug: nextjs-file-structure
title: Next.js 파일구조 스텝 바이스텝
authors: gimso2x
tags: [Next.js]
---

## Next.js 기본 설치

설치목록

- Next.js
- Eslint
  - @typescript-eslint/eslint-plugin
  - eslint-config-prettier
- Prettier
- @next/bundle-analyzer
- cross-env - Window, Mac 크로스 개발환경  Node
- rimraf - Window, Mac 크로스 개발환경 폴더지우기
- tsc-watch - typescript 개발을 위해

## 1. Next.js 설치

```jsx
npx create-next-app@latest --typescript
```

## 2. Eslint, Prettier 패키지 설치

```jsx
npm i -D @typescript-eslint/eslint-plugin prettier eslint-config-prettier
```

## 3. Vscode 세팅

```jsx
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "editor.formatOnSave": true, // Tell VSCode to format files on save
  "editor.defaultFormatter": "esbenp.prettier-vscode" // Tell VSCode to use Prettier as default file formatter
}
```

## 4. Eslint 설정

```jsx
// .eslintrc.json
{
  "extends": [
    "next/core-web-vitals",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "rules": {
    "@typescript-eslint/no-unused-vars": "error",
    "@typescript-eslint/no-explicit-any": "error"
  }
}
```

## 5. Prettier 세팅

```jsx
// .prettierrc.json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false,
  "printWidth": 100
}
```

## 6. root(/)에 src폴더 생성 pages, styles 위치 이동

```jsx
// before
└─/
    ├─pages
    └─styles

// after
└─/
 └─src
    ├─pages
    └─styles
```

## 7. tsc-watch 설치

```jsx
npm i -D tsc-watch

// .package.json
"scripts": {
  "dev": "next dev",
  "dev:ts": "tsc-watch --onSuccess \"npm run dev\"",
 ...
},
```

## 8. tsconfig.js 수정

```jsx
// .tsconfig.js
"compilerOptions": {
    "baseUrl": ".", /* 절대경로 모듈이 아닌, 모듈이 위치한 기준 디렉토리 */
    "paths": { /* baseUrl 기준으로 불러올 모듈의 위치를 재지정하는 엔트리 */
      "@/*": [
        "src/*"
      ]
    },
  ...
 }
```

## 9. next bundle analzyer 설치

```jsx
npm i -D @next/bundle-analyzer cross-env rimraf
```

```jsx
// .next.config.js
const {
  PHASE_DEVELOPMENT_SERVER,
  PHASE_PRODUCTION_BUILD,
  PHASE_PRODUCTION_SERVER,
  // eslint-disable-next-line @typescript-eslint/no-var-requires
} = require('next/constants');

// eslint-disable-next-line @typescript-eslint/no-var-requires
const withBundleAnalyzer = require('@next/bundle-analyzer')({
  enabled: process.env.ANALYZE === 'true',
});

module.exports = (phase, { defaultConfig }) => {
  const isDevLocal = phase === PHASE_DEVELOPMENT_SERVER; // `npm run dev`
  const isDevServer =
    !process.env.PROD && (phase === PHASE_PRODUCTION_BUILD || phase === PHASE_PRODUCTION_SERVER); // `npm run build`
  const isProdServer =
    process.env.PROD && (phase === PHASE_PRODUCTION_BUILD || phase === PHASE_PRODUCTION_SERVER); // `npm run build:prod`

  console.log(
    `isDevLocal:${isDevLocal}  isDevServer:${isDevServer}   isProdServer:${isProdServer}`
  );

  const currentEnv = () => {
    if (isDevLocal) return 'DevLocal';
    if (isDevServer) return 'DevServer';
    if (isProdServer) return 'ProdServer';
  };

  /** @type {import('next').NextConfig} */
  const nextConfig = {
    reactStrictMode: true,
    swcMinify: true,
    env: {
      currentEnv: currentEnv(),
    },
  };

  const plugins = [withBundleAnalyzer];
  const config = plugins.reduce((acc, next) => next(acc), {
    ...nextConfig,
  });
  return config;
};
```

```jsx
// .package.json
...
 "scripts": {
  ...
    "build-stats": "cross-env ANALYZE=true npm run build",
    "clean": "rimraf .next out"
  ...
  },
```

## prettier css order

<https://github.com/Siilwyn/prettier-plugin-css-order>

## 10. 원스톱 설치

### npm

```jsx
npm i -D @typescript-eslint/eslint-plugin prettier eslint-config-prettier tsc-watch @next/bundle-analyzer cross-env rimraf
```

### package.json

```json
"scripts": {
    "dev": "next dev",
    "dev:ts": "tsc-watch --onSuccess \"npm run dev\"",
    "build": "next build",
    "build-stats": "cross-env ANALYZE=true npm run build",
    "start": "next start",
    "lint": "next lint",
    "clean": "rimraf .next out"
  },
```

## Trouble shooting

### 1. next13 설치후 eslint, eslint-config-next 추가설치

```jsx
// error message
> aipartner@0.1.0 lint
> next lint

Failed to load config "next/core-web-vitals" to extend from.
Referenced from: C:\work\aipartner\.eslintrc.json
```

#### 참조링크

[https://github.com/ixartz/Next-js-Boilerplate](https://github.com/ixartz/Next-js-Boilerplate)

[Start a clean Next.js project with TypeScript, ESLint and Prettier](https://paulintrognon.fr/blog/typescript-prettier-eslint-next-js)
