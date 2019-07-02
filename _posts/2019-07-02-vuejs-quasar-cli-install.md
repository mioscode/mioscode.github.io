---
title: "(Vue.js) Quasar 1.0 CLI 설치하기"
categories:
  -  Quasar
tags:
  - Vue.js
  - Quasar
comments: true
---

# 0. 환경
node >= 8, npm >= 5 설치되어있는지 확인한다.
```
$ npm version    
{ npm: '6.4.1',
  ares: '1.15.0',
  cldr: '33.1',
  http_parser: '2.8.0',
  icu: '62.1',
  modules: '64',
  napi: '3',
  nghttp2: '1.34.0',
  node: '10.15.3',
  openssl: '1.1.0j',
  tz: '2018e',
  unicode: '11.0',
  uv: '1.23.2',
  v8: '6.8.275.32-node.51',
  zlib: '1.2.11' }
```
```
$ node -v
v10.15.3
````

# 1. Quasar CLI 설치
Uninstall quasar-cli if you have it from <1.0 versions
```
$ npm uninstall -g quasar-cli
```

Node.js >= 8.9.0 is required.
```
$ npm install -g @quasar/cli
```
v1.0 + CLI는 v1.0 이전 프로젝트 폴더와도 호환되므로 이전 프로젝트가 더 이상 실행되지 않는다고 걱정할 필요 없다.
Quasar 프로젝트 폴더를 생성하기 위해 vue cli를  더 이상 설치하지 않아도 된다.

# 2. Quasar 프로젝트 생성
```
$ quasar create <ProjectName>
  ___                             
 / _ \ _   _  __ _ ___  __ _ _ __ 
| | | | | | |/ _` / __|/ _` | '__|
| |_| | |_| | (_| \__ \ (_| | |   
 \__\_\\__,_|\__,_|___/\__,_|_|   

? Project name (internal usage for dev) project_name
? Project product name (official name; must start with a letter if you will build mobile apps) Project App
? Project description A Quasar Framework app
? Author admin <admin@test.com>
? Check the features needed for your project: (Press <space> to select, <a> to toggle all, <i> to invert selection)ESLint,
 Vuex, Axios, Vue-i18n, IE11 support
? Pick an ESLint preset Standard
? Cordova id (disregard if not building mobile apps) org.cordova.quasar.app
? Should we run `npm install` for you after the project has been created? (recommended) NPM

...

 [*] Quasar Project initialization finished!

To get started:

  cd ArgusPoC
  quasar dev

Documentation can be found at: https://quasar.dev

Quasar is relying on donations to evolve. We'd be very grateful if you can
read our manifest on "Why donations are important": https://quasar.dev/why-donate
Donation campaign: https://donate.quasar.dev
Any amount is very welcomed.
If invoices are required, please first contact razvan@quasar.dev

Please give us a star on Github if you appreciate our work:
https://github.com/quasarframework/quasar

Enjoy! - Quasar Team

```

# 3. 실행
```
$ cd ProjectName
$ quasar dev
...
 app:dev-server Opening default browser at http://localhost:8080/ +11s
```

# Reference
<https://quasar.dev/quasar-cli/installation>
<https://godffs.tistory.com/3268>