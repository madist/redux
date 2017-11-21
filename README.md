# <a href='http://redux.js.org'><img src='https://camo.githubusercontent.com/f28b5bc7822f1b7bb28a96d8d09e7d79169248fc/687474703a2f2f692e696d6775722e636f6d2f4a65567164514d2e706e67' height='60'></a>

Redux는 JavaScript 애플리케이션을위한 예측 가능한 상태 컨테이너입니다.  
(워드프레스 프레임웍과 혼동하지 마세요. – [Redux Framework](https://reduxframework.com/).)

Redux는 일관성있게 작동하고 다양한 환경 (클라이언트, 서버 및 기본)에서 실행되는 응용 프로그램을 작성하고 테스트하기 쉽도록 도와줍니다. 그뿐 아니라 다음과 같은 훌륭한 개발자 경험을 제공합니다. [live code editing combined with a time traveling debugger](https://github.com/gaearon/redux-devtools).

당신은 [React](https://facebook.github.io/react/)와 함께 Redux 를 사용할 수 있습니다. 물론, 다른 렌더링 라이브러리와 함께 사용할 수도 있죠.  

Redux는 작습니다. (2kB, 의존성을 포함한 크기).

[![build status](https://img.shields.io/travis/reactjs/redux/master.svg?style=flat-square)](https://travis-ci.org/reactjs/redux)
[![npm version](https://img.shields.io/npm/v/redux.svg?style=flat-square)](https://www.npmjs.com/package/redux)
[![npm downloads](https://img.shields.io/npm/dm/redux.svg?style=flat-square)](https://www.npmjs.com/package/redux)
[![redux channel on discord](https://img.shields.io/badge/discord-%23redux%20%40%20reactiflux-61dafb.svg?style=flat-square)](https://discord.gg/0ZcbPKXt5bZ6au5t)
[![#rackt on freenode](https://img.shields.io/badge/irc-%23rackt%20%40%20freenode-61DAFB.svg?style=flat-square)](https://webchat.freenode.net/)
[![Changelog #187](https://img.shields.io/badge/changelog-%23187-lightgrey.svg?style=flat-square)](https://changelog.com/187)

>**Redux창시자로부터 Redux 배우기:**  
>**[Part 1: Getting Started with Redux](https://egghead.io/series/getting-started-with-redux) (30 free videos)**<br>
>**[Part 2: Building React Applications with Idiomatic Redux](https://egghead.io/courses/building-react-applications-with-idiomatic-redux) (27 free videos)**

### 사용자 평가 

>[“Love what you're doing with Redux”](https://twitter.com/jingc/status/616608251463909376)  
>Jing Chen, creator of Flux

>[“I asked for comments on Redux in FB's internal JS discussion group, and it was universally praised. Really awesome work.”](https://twitter.com/fisherwebdev/status/616286955693682688)  
>Bill Fisher, author of Flux documentation

>[“It's cool that you are inventing a better Flux by not doing Flux at all.”](https://twitter.com/andrestaltz/status/616271392930201604)  
>André Staltz, creator of Cycle

### 계속 진행하기 전에

>**Also read:**  
>**[당신은 Redux 필요하지 않을 수도 있습니다](https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367)**

### 개발자 경험

나는 Redux 를 사용하였습니다. Europe Talk 리액트 작업
 [“Hot Reloading with Time Travel”](https://www.youtube.com/watch?v=xsSnOQynTHs)을 할때요. 내 목표는 최소한의 API로 상태 관리 라이브러리를 만드는 것이 었습니다. 물론, 완벽한 행동 예측을 통해서 로깅, 핫 리로딩, 시간 여행, 범용 앱, 기록 및 재생을 구현할 수 있습니다. 

### 영향

Redux는 [Flux](http://facebook.github.io/flux/)의 아이디어를 발전 시켰습니다. Redux는 [Elm](https://github.com/evancz/elm-architecture-tutorial/)으로부터 영감을 얻어 Flux 의 복잡성을 개선하였습니다.  
사용 여부와 관계없이 Redux는 시작하는 데 몇 분 밖에 걸리지 않습니다.

### 설치

안정화 버전 설치:

```
npm install --save redux
```

여기서는 패키지 관리자로 [npm](https://www.npmjs.com/)을 사용한다고 가정합니다.  

그렇지 않은 경우 [unpkg](https://unpkg.com/redux/), 다운로드하거나 패키지 관리자를 설정할 수 있습니다.

가장 일반적으로 사람들은 [CommonJS](http://webpack.github.io/docs/commonjs.html) 모듈 모음으로 Redux를 사용합니다. 이러한 모듈은 [Webpack](https://webpack.js.org/), [Browserify](http://browserify.org/) 또는 노드 환경에서`redux`를 가져올 때 얻을 수있는 모듈입니다. 물론, Redux는 [Rollup](http://rollupjs.org) 모듈 또한 지원합니다.

모듈 번들을 사용하지 않는다면 괜찮습니다. `redux` npm 패키지에는 [dist](https://unpkg.com/redux/dist/)에 미리 컴파일 된 제작 및 개발 [UMD](https://github.com/umdjs/umd) 빌드가 포함되어 있습니다. 그들은 번들러없이 직접 사용할 수 있으므로 많은 인기있는 JavaScript 모듈 로더 및 환경과 호환됩니다. 예를 들어 UMD 빌드를 페이지의 [`<script>`태그](https://unpkg.com/redux/dist/redux.js) 또는 [Bower을 통한 설치](https://github.com/reactjs/redux/pull/1181#issuecomment-167361975). UMD 빌드는 Redux를`window.Redux` 글로벌 변수로 사용할 수 있도록합니다.

Redux 소스 코드는 ES2015로 작성되었지만 CommonJS 및 UMD 빌드를 모두 ES5로 사전 컴파일하여 [모든 최신 브라우저](http://caniuse.com/#feat=es5)에서 작동합니다. [Redux 시작하기](https://github.com/reactjs/redux/blob/master/examples/counter-vanilla/index.html)에는 Babel이나 모듈 번들러를 사용할 필요가 없습니다.

#### Redux를 하는데 함께 쓰면 좋은 패키지

대부분의 경우 [React bindings](https://github.com/reactjs/react-redux) 및 [developer tools](https://github.com/gaearon/redux-devtools)도 필요합니다.

```
npm install --save react-redux
npm install --save-dev redux-devtools
```

Redux 자체와 달리 Redux 에코 시스템의 많은 패키지는 UMD 빌드를 제공하지 않으므로 [Webpack](https://webpack.js.org/) 및 [Browserify](http://browserify.org/)와 같은 CommonJS 모듈 번들을 사용을 통하여 편안한 개발 경험을 얻을 수 있습니다.

### 요점

1. 앱의 전체 상태는 단일 *`스토어`* 내의 오브젝트 트리에 저장됩니다.
2. 상태 트리를 변경하는 유일한 방법은 어떤 일이 일어 났는지 설명하는 객체 인 *`action`* 을 내보내는 것입니다.
3. 동작이 상태 트리를 변환하는 방법을 지정하려면 순수한 *`reducers`* 를 작성합니다.

이게 전부다!

```js
import { createStore } from 'redux'

/**
 * 이것은 Reducer 입니다, (state, action) => state 구조의 순수 함수입니다.
 * 액션이 상태를 다음 상태로 변환하는 방법을 설명합니다.
 *
 * 상태의 모양은 다양합니다 : state는 프리미티브, 배열, 객체 일 수 있습니다.
 * 또는 Immutable.js 데이터 구조도 가능합니다. 중요한 것은 상태 객체를 직접 변경해서는 안됩니다. 상태가 변경되면 기존객체를 바꾸는 것이 아니라, 새로운 객체를 반환해야합니다.
 *
 * 이 예제에서 우리는`switch` 문과 문자열을 사용합니다. 그러나 프로젝트에 적합한 경우 다른 규칙 (예 : 함수 맵)을 따르는 helper를 사용해도 좋습니다.
 */
function counter(state = 0, action) {
  switch (action.type) {
  case 'INCREMENT':
    return state + 1
  case 'DECREMENT':
    return state - 1
  default:
    return state
  }
}

// Redux Store 를 생성하여 앱의 상태를 저장합니다.
// API 는 { subscribe, dispatch, getState } 이 있습니다.
let store = createStore(counter)

// 상태 변경에 대한 응답으로 subscribe()를 사용하여 UI를 업데이트 할 수 있습니다.
// 일반적으로 직접 subscribe()하지 않고 뷰 바인딩 라이브러리 (예 : React Redux)를 사용합니다.
// 그러나 localStorage에서 현재 상태를 유지하는 것이 또한 편리 할 수 있습니다.

store.subscribe(() =>
  console.log(store.getState())
)

// 내부 상태를 변경하는 유일한 방법은 작업을 전달하는 것입니다.
// dispatch(`action`)
// action 들은 직력화될 수도 있고, 로깅 및 저장되어 Replay 될 수 있습니다.
store.dispatch({ type: 'INCREMENT' })
// 1
store.dispatch({ type: 'INCREMENT' })
// 2
store.dispatch({ type: 'DECREMENT' })
// 1
```

상태를 직접 변경하는 대신 *`actions`* 라는 일반 객체를 사용하여 발생시키고 자하는 상태변화를 설정합니다. 그런 다음 *`reducer`* 라는 특수 함수를 작성합니다. 이 특수 함수(`reducer`)는 모든 작업이 전체 응용 프로그램의 상태를 변환하는 방법을 결정합니다.

Flux와 비교할경우, 이해해야 할 중요한 차이점이 하나 있습니다. Redux에는 `Dispatcher` 나 많은 `Store`를 지원하지 않습니다. 대신 단일 루트 축소 기능을 가진 단일 `Store`가 있습니다. 앱이 커지면 `Store`을 추가하는 대신 루트 트리머를 상태 트리의 다른 부분에서 독립적으로 작동하는 작은 `Reducer` 로 분리합니다. 이는 React 앱에 하나의 루트 `Component`가 있는 것과 동일하지만, 많은 작은 `Component`로 구성됩니다.

이 아키텍쳐는 `Counter 앱` 에는 너무 오버스펙일 수 있습니다. 그러나, 크고 복잡한 앱들의 경우 이 디자인 패턴은 높은 효율을 보여줄 것입니다. 또한, 이 패턴은 모든 상태변화에 따른 추적이 가능하여, 강력한 개발툴을 제공할 수 있습니다. 
여러분은 유저의 세션을 저장하고, 모든 액션들을 재현할 수 있습니다. 

### 창시자에게 Redux 배우기

[Getting Started with Redux](https://egghead.io/series/getting-started-with-redux) is a video course consisting of 30 videos narrated by Dan Abramov, author of Redux. It is designed to complement the “Basics” part of the docs while bringing additional insights about immutability, testing, Redux best practices, and using Redux with React. **This course is free and will always be.**

>[“Great course on egghead.io by @dan_abramov - instead of just showing you how to use #redux, it also shows how and why redux was built!”](https://twitter.com/sandrinodm/status/670548531422326785)  
>Sandrino Di Mattia

>[“Plowing through @dan_abramov 'Getting Started with Redux' - its amazing how much simpler concepts get with video.”](https://twitter.com/chrisdhanaraj/status/670328025553219584)  
>Chris Dhanaraj

>[“This video series on Redux by @dan_abramov on @eggheadio is spectacular!”](https://twitter.com/eddiezane/status/670333133242408960)  
>Eddie Zaneski

>[“Come for the name hype. Stay for the rock solid fundamentals. (Thanks, and great job @dan_abramov and @eggheadio!)”](https://twitter.com/danott/status/669909126554607617)  
>Dan

>[“This series of videos on Redux by @dan_abramov is repeatedly blowing my mind - gunna do some serious refactoring”](https://twitter.com/gelatindesign/status/669658358643892224)  
>Laurence Roberts

So, what are you waiting for?

#### [Watch the 30 Free Videos!](https://egghead.io/series/getting-started-with-redux)

If you enjoyed my course, consider supporting Egghead by [buying a subscription](https://egghead.io/pricing). Subscribers have access to the source code of every example in my videos and tons of advanced lessons on other topics, including JavaScript in depth, React, Angular, and more. Many [Egghead instructors](https://egghead.io/instructors) are also open source library authors, so buying a subscription is a nice way to thank them for the work that they've done.

### 문서

* [소개](https://madist.gitbooks.io/redux-ko/content/docs/introduction/index.html)
* [기본](https://madist.gitbooks.io/redux-ko/content/docs/basics/index.html)
* [고급](https://madist.gitbooks.io/redux-ko/content/docs/advanced/index.html)
* [따라하기](https://madist.gitbooks.io/redux-ko/content/docs/recipes/index.html)
* [FAQ](https://madist.gitbooks.io/redux-ko/content/docs/FAQ.html)
* [문제해결](https://madist.gitbooks.io/redux-ko/content/docs/Troubleshooting.html)
* [용어해설](https://madist.gitbooks.io/redux-ko/content/docs/Glossary.html)
* [API 문서](https://madist.gitbooks.io/redux-ko/content/docs/api/index.html)

For PDF, ePub, and MOBI exports for offline reading, and instructions on how to create them, please see: [paulkogel/redux-offline-docs](https://github.com/paulkogel/redux-offline-docs).

For Offline docs, please see: [devdocs](http://devdocs.io/redux/)

### 예제

Almost all examples have a corresponding CodeSandbox sandbox. This is an interactive version of the code that you can play with online.

* [Counter Vanilla](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#counter-vanilla) ([source](https://github.com/reactjs/redux/tree/master/examples/counter-vanilla))
* [Counter](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#counter) ([source](https://github.com/reactjs/redux/tree/master/examples/counter), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/counter))
* [Todos](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#todos) ([source](https://github.com/reactjs/redux/tree/master/examples/todos), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todos))
* [Todos with Undo](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#todos-with-undo) ([source](https://github.com/reactjs/redux/tree/master/examples/todos-with-undo), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todos-with-undo))
* [TodoMVC](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#todomvc) ([source](https://github.com/reactjs/redux/tree/master/examples/todomvc), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todomvc))
* [Shopping Cart](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#shopping-cart) ([source](https://github.com/reactjs/redux/tree/master/examples/shopping-cart), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/shopping-cart))
* [Tree View](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#tree-view) ([source](https://github.com/reactjs/redux/tree/master/examples/tree-view), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/tree-view))
* [Async](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#async) ([source](https://github.com/reactjs/redux/tree/master/examples/async), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/async))
* [Universal](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#universal) ([source](https://github.com/reactjs/redux/tree/master/examples/universal))
* [Real World](https://madist.gitbooks.io/redux-ko/content/docs/introduction/Examples.html#real-world) ([source](https://github.com/reactjs/redux/tree/master/examples/real-world), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/real-world))

If you're new to the NPM ecosystem and have troubles getting a project up and running, or aren't sure where to paste the gist above, check out [simplest-redux-example](https://github.com/jackielii/simplest-redux-example) that uses Redux together with React and Browserify.

### 토의

Join the [#redux](https://discord.gg/0ZcbPKXt5bZ6au5t) channel of the [Reactiflux](http://www.reactiflux.com) Discord community.

### Thanks

* [The Elm Architecture](https://github.com/evancz/elm-architecture-tutorial) for a great intro to modeling state updates with reducers;
* [Turning the database inside-out](http://www.confluent.io/blog/turning-the-database-inside-out-with-apache-samza/) for blowing my mind;
* [Developing ClojureScript with Figwheel](https://www.youtube.com/watch?v=j-kj2qwJa_E) for convincing me that re-evaluation should “just work”;
* [Webpack](https://webpack.js.org/concepts/hot-module-replacement/) for Hot Module Replacement;
* [Flummox](https://github.com/acdlite/flummox) for teaching me to approach Flux without boilerplate or singletons;
* [disto](https://github.com/threepointone/disto) for a proof of concept of hot reloadable Stores;
* [NuclearJS](https://github.com/optimizely/nuclear-js) for proving this architecture can be performant;
* [Om](https://github.com/omcljs/om) for popularizing the idea of a single state atom;
* [Cycle](https://github.com/cyclejs/cycle-core) for showing how often a function is the best tool;
* [React](https://github.com/facebook/react) for the pragmatic innovation.

Special thanks to [Jamie Paton](http://jdpaton.github.io) for handing over the `redux` NPM package name.

### 로고

You can find the official logo [on GitHub](https://github.com/reactjs/redux/tree/master/logo).

### Change Log

This project adheres to [Semantic Versioning](http://semver.org/).  
Every release, along with the migration instructions, is documented on the Github [Releases](https://github.com/reactjs/redux/releases) page.

### Patrons

The work on Redux was [funded by the community](https://www.patreon.com/reactdx).  
Meet some of the outstanding companies that made it possible:

* [Webflow](https://github.com/webflow)
* [Ximedes](https://www.ximedes.com/)

[See the full list of Redux patrons](PATRONS.md), as well as the always-growing list of [people and companies that use Redux](https://github.com/reactjs/redux/issues/310).

### License

MIT
