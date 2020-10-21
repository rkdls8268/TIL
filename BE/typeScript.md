# <center>TypeScript</center>

## TypeScript

JavaScript 기반의 언어. **컴파일을 하면 JS가 되는 언어**이다. 
둘의 주요 차이점은 JS는 클라이언트 측 스크립팅 언어이고 TS는 객체 지향 컴파일 언어이다.

### 📌TS의 주요 장점

* 클래스 기반 객체를 만들 수 있다는 것. C++, Java 등에서 사용할 수 있는 클래스, 객체, 상속과 같은 개념을 모두 사용할 수 있음.
* TS는 JS의 상위 집합이므로 JS의 모든 기능을 사용할 수 있다.
* 타입 지정이 가능하며 컴파일 시간에 타입 체크

TS와 같은 변환 언어의 중요한 장점 중 하나는 기능이 추가된다는 것. 즉, 인터페이스와 추상 클래스, 대수, 데이터 타입 등의 기능을 자바스크립트에 더하며, 다른 라이브러리들을 추가적으로 사용하지 않아도 된다

## DEMO

### Initial Project 

```
$ mkdir typescript_practice 

// 해당 디렉토리로 이동 후
$ npm init -y
```

### 설치

```
$ npm install -g express

// 되도록이면 global로 설치해주자😉
$ npm install -g typescript
```

### @types
모듈을 설치할 때 항상 TypeScript를 지원하거나 @types에서 모듈이 있는지 확인하는 것이 좋다.
만약 없다면, 직접 .d.ts 파일을 만들어야 한다.
```
$ npm install -g @types/node @types/express
```

### 빌드 설정
```
$ npx tsc -init
```

### 옵션 설정
```
//tsconfig.json
{
  "compilerOptions": {
    /* Visit https://aka.ms/tsconfig.json to read more about this file */

    /* Basic Options */
    "target": "es5",                          /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019', 'ES2020', or 'ESNEXT'. */
    "module": "commonjs",                     /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', 'es2020', or 'ESNext'. */
    "outDir": "dist",                        /* Redirect output structure to the 

    /* Strict Type-Checking Options */
    "strict": true,                           /* Enable all strict type-checking options. */

    /* Module Resolution Options */
    "moduleResolution": "node",            /* Specify module resolution strategy: 'node' (Node.js) or 'classic' (TypeScript pre-1.6). */

    "skipLibCheck": true,                     /* Skip type checking of declaration files. */
    "forceConsistentCasingInFileNames": true  /* Disallow inconsistently-cased references to the same file. */
  },
  "include": [
    "src/**/*"
  ]
}
```

✔️ 'express is not callable' 오류 발생 
"esModuleInterop": true 주석 처리

### TypeScript 빌드 후 Node.js로 실행하는 스크립트 추가 
```
//package.json
  "scripts": {
    "start": "tsc && node dist",
    "build": "tsc"
  },
```

### Express 시작하기
```
// src/index.ts
import * as express from 'express';

const app = express();

app.get('/', (req: express.Request, res: express.Response) => {
    res.send('Hello World!');
});

app.listen(3000, () => {
    console.log('Example app listening on port 3000!');
});

// 이거 컴파일하면 dist/index.js 경로에 파일이 생성된다. 
// 이때 ts 파일에서 명시한 값의 타입이 컴파일이 되는 과정에서는 모두 사라지게 된다. 
```

```
// dist/index.js
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
// var express = require('express');
var express = require("express"); // 1
var app = express();
app.get('/', function (req, res) {
    res.send('Hello World!');
});
app.listen(3000, function () {
    console.log('Example app listening on port 3000!');
});
// 이거 컴파일하면 dist/index.js 경로에 파일이 생성된다. 
// 이때 ts 파일에서 명시한 값의 타입이 컴파일이 되는 과정에서는 모두 사라지게 된다. 
```

### 서버 실행
```
$ npm start
```