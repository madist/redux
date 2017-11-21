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
 * This is a reducer, a pure function with (state, action) => state signature.
 * It describes how an action transforms the state into the next state.
 *
 * The shape of the state is up to you: it can be a primitive, an array, an object,
 * or even an Immutable.js data structure. The only important part is that you should
 * not mutate the state object, but return a new object if the state changes.
 *
 * In this example, we use a `switch` statement and strings, but you can use a helper that
 * follows a different convention (such as function maps) if it makes sense for your
 * project.
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

// Create a Redux store holding the state of your app.
// Its API is { subscribe, dispatch, getState }.
let store = createStore(counter)

// You can use subscribe() to update the UI in response to state changes.
// Normally you'd use a view binding library (e.g. React Redux) rather than subscribe() directly.
// However it can also be handy to persist the current state in the localStorage.

store.subscribe(() =>
  console.log(store.getState())
)

// The only way to mutate the internal state is to dispatch an action.
// The actions can be serialized, logged or stored and later replayed.
store.dispatch({ type: 'INCREMENT' })
// 1
store.dispatch({ type: 'INCREMENT' })
// 2
store.dispatch({ type: 'DECREMENT' })
// 1
```

Instead of mutating the state directly, you specify the mutations you want to happen with plain objects called *actions*. Then you write a special function called a *reducer* to decide how every action transforms the entire application's state.

If you're coming from Flux, there is a single important difference you need to understand. Redux doesn't have a Dispatcher or support many stores. Instead, there is just a single store with a single root reducing function. As your app grows, instead of adding stores, you split the root reducer into smaller reducers independently operating on the different parts of the state tree. This is exactly like how there is just one root component in a React app, but it is composed out of many small components.

This architecture might seem like an overkill for a counter app, but the beauty of this pattern is how well it scales to large and complex apps. It also enables very powerful developer tools, because it is possible to trace every mutation to the action that caused it. You can record user sessions and reproduce them just by replaying every action.

### Learn Redux from Its Creator

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

### Documentation

* [Introduction](http://redux.js.org/docs/introduction/index.html)
* [Basics](http://redux.js.org/docs/basics/index.html)
* [Advanced](http://redux.js.org/docs/advanced/index.html)
* [Recipes](http://redux.js.org/docs/recipes/index.html)
* [FAQ](http://redux.js.org/docs/FAQ.html)
* [Troubleshooting](http://redux.js.org/docs/Troubleshooting.html)
* [Glossary](http://redux.js.org/docs/Glossary.html)
* [API Reference](http://redux.js.org/docs/api/index.html)

For PDF, ePub, and MOBI exports for offline reading, and instructions on how to create them, please see: [paulkogel/redux-offline-docs](https://github.com/paulkogel/redux-offline-docs).

For Offline docs, please see: [devdocs](http://devdocs.io/redux/)

### Examples

Almost all examples have a corresponding CodeSandbox sandbox. This is an interactive version of the code that you can play with online.

* [Counter Vanilla](http://redux.js.org/docs/introduction/Examples.html#counter-vanilla) ([source](https://github.com/reactjs/redux/tree/master/examples/counter-vanilla))
* [Counter](http://redux.js.org/docs/introduction/Examples.html#counter) ([source](https://github.com/reactjs/redux/tree/master/examples/counter), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/counter))
* [Todos](http://redux.js.org/docs/introduction/Examples.html#todos) ([source](https://github.com/reactjs/redux/tree/master/examples/todos), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todos))
* [Todos with Undo](http://redux.js.org/docs/introduction/Examples.html#todos-with-undo) ([source](https://github.com/reactjs/redux/tree/master/examples/todos-with-undo), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todos-with-undo))
* [TodoMVC](http://redux.js.org/docs/introduction/Examples.html#todomvc) ([source](https://github.com/reactjs/redux/tree/master/examples/todomvc), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todomvc))
* [Shopping Cart](http://redux.js.org/docs/introduction/Examples.html#shopping-cart) ([source](https://github.com/reactjs/redux/tree/master/examples/shopping-cart), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/shopping-cart))
* [Tree View](http://redux.js.org/docs/introduction/Examples.html#tree-view) ([source](https://github.com/reactjs/redux/tree/master/examples/tree-view), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/tree-view))
* [Async](http://redux.js.org/docs/introduction/Examples.html#async) ([source](https://github.com/reactjs/redux/tree/master/examples/async), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/async))
* [Universal](http://redux.js.org/docs/introduction/Examples.html#universal) ([source](https://github.com/reactjs/redux/tree/master/examples/universal))
* [Real World](http://redux.js.org/docs/introduction/Examples.html#real-world) ([source](https://github.com/reactjs/redux/tree/master/examples/real-world), [sandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/real-world))

If you're new to the NPM ecosystem and have troubles getting a project up and running, or aren't sure where to paste the gist above, check out [simplest-redux-example](https://github.com/jackielii/simplest-redux-example) that uses Redux together with React and Browserify.

### Discussion

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

### Logo

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
