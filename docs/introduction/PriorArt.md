# 선행기술

Redux에는 혼합 유산이 있습니다. 이는 일부 패턴 및 기술과 유사하지만 중요한 측면에서 서로 다릅니다. 유사점과 차이점을 아래에서 살펴 보겠습니다.

### Flux

`Redux`를 [Flux](https://facebook.github.io/flux/)의 구현으로 간주할 수 있습니까?
[네](https://twitter.com/fisherwebdev/status/616278911886884864), and [아니오](https://twitter.com/andrestaltz/status/616270755605708800).

(Don't worry, [Flux creators](https://twitter.com/jingc/status/616608251463909376) [approve of it](https://twitter.com/fisherwebdev/status/616286955693682688), if that's all you wanted to know.)

Redux는 Flux의 몇 가지 중요한 특성에서 영감을 얻었습니다. Flux와 마찬가지로 Redux는 모델 업데이트 논리를 응용 프로그램의 특정 계층 (Flux의 "store", Redux의 "reducer")에 집중 시키도록 규정합니다. 애플리케이션 코드가 데이터를 직접 변이시키는 대신, 모든 변이를 "액션 (action)"이라 불리는 평범한 객체로 기술하라.

Flux와는 달리 **`Redux에는 Dispatcher`** 개념이 없습니다. 이는 Event Emitter 대신 순수 함수(`reducer`)에 의존하고 순수 함수는 작성하기 쉽고 이를 관리하는 추가 엔티티가 필요하지 않기 때문입니다. Flux를 보는 방법에 따라 편차 또는 구현 세부 사항으로 볼 수 있습니다. Flux 의 경우 다음처럼 묘사됩니다. [described as `(state, action) => state`](https://speakerdeck.com/jmorrell/jsconf-uy-flux-those-who-forget-the-past-dot-dot-dot-1). 이런 관점에서, Redux 는 Flux의 아키텍쳐를 따르고 있습니다.그러나, Redux 는 `reducer`에 의해서 더 간단해집니다.

Flux와 보다 더 중요한 차이점이라면, Redux는 직접적으로 상태를 수정하지 않습니다. 평범한 object와 array를 상태로 사용할 수는 있지만, reducer 내부에서 해당 `action` 을 변경시키지 않는 것이 좋습니다. 당신은 [객체 연산자](../recipes/UsingObjectSpreadOperator.md), 혹은 [Immutable](https://facebook.github.io/immutable-js) 라이브러리를 이용해서  항상 기존의 상태가 아닌 새로운 상태값을 반환해야합니다.

기술적으로는 성능 향상을 위한 [순수하지 않은 reducer](https://github.com/reactjs/redux/issues/328#issuecomment-125035516) *`가능합니다`*.그러나, 이런 행위를 우리는 권장하지 않습니다. 
개발 지원기능들 중 `시간여행,녹화/재생,실시간 리로딩`와 같은 기능들이 동작하지 않을 것입니다.
또한 [Omu](https://github.com/omcljs/om)에서 보여 주듯이 객체 할당을 잃으면서 성능에 있어 불리할지라도, `reducer`의 `purity` 덕분에 정확히 무엇이 바뀌 었는지 알 수 있고, 이는 값 비싼 재렌더링 및 재계산을 피할 수 있기에 더 낫습니다.

### Elm

[Elm](http://elm-lang.org/)은 Haskell 언어에 영감을 받아 [Evan Czaplicki](https://twitter.com/czaplic)이 만든 함수형 개발 언어 입니다. `Elm`은 [a “model view update” architecture](https://github.com/evancz/elm-architecture-tutorial/)을 강제합니다. 업데이트는 다음과 같이 진행합니다 : `(action, state) => state`. `Elm`의 *`updaters`* 는 `Redux`의 *`reducer`* 와 목적이 같습니다.

Redux와는 달리, Elm은 언어이므로 purity, 정적유형지정, out of the box immutability 및 패턴 일치 (`case` 표현식 사용)와 같은 여러 가지 이점을 누릴 수 있습니다. `Elm`언어를 이용하여 개발하지 않더라도, 한번 아키텍쳐를 읽고, 사용해 보세요. 우리는 Redux에서 영감을 얻으 려합니다. Elm의 정적 타이핑에 더 가까워 질 수있는 한 가지 방법은 [Flow와 같은 점진적인 타이핑 솔루션을 사용하는 것](https://github.com/reactjs/redux/issues/290)입니다.

### 불변

[Immutable](https://facebook.github.io/immutable-js) 은 영속 데이터 구조를 구현한 자바스크립트 라이브러리입니다. It is performant and has an idiomatic JavaScript API.

Immutable and most similar libraries are orthogonal to Redux. Feel free to use them together!

**Redux doesn't care *how* you store the state—it can be a plain object, an Immutable object, or anything else.** You'll probably want a (de)serialization mechanism for writing universal apps and hydrating their state from the server, but other than that, you can use any data storage library *as long as it supports immutability*. For example, it doesn't make sense to use Backbone for Redux state, because Backbone models are mutable.

Note that, even if your immutable library supports cursors, you shouldn't use them in a Redux app. The whole state tree should be considered read-only, and you should use Redux for updating the state, and subscribing to the updates. Therefore writing via cursor doesn't make sense for Redux. **If your only use case for cursors is decoupling the state tree from the UI tree and gradually refining the cursors, you should look at selectors instead.** Selectors are composable getter functions. See [reselect](http://github.com/faassen/reselect) for a really great and concise implementation of composable selectors.

### Baobab

[Baobab](https://github.com/Yomguithereal/baobab) is another popular library implementing immutable API for updating plain JavaScript objects. While you can use it with Redux, there is little benefit in using them together.

Most of the functionality Baobab provides is related to updating the data with cursors, but Redux enforces that the only way to update the data is to dispatch an action. Therefore they solve the same problem differently, and don't complement each other.

Unlike Immutable, Baobab doesn't yet implement any special efficient data structures under the hood, so you don't really win anything from using it together with Redux. It's easier to just use plain objects in this case.

### RxJS

[RxJS](https://github.com/ReactiveX/RxJS) is a superb way to manage the complexity of asynchronous apps. In fact [there is an effort to create a library that models human-computer interaction as interdependent observables](http://cycle.js.org).

Does it make sense to use Redux together with RxJS? Sure! They work great together. For example, it is easy to expose a Redux store as an observable:

```js
function toObservable(store) {
  return {
    subscribe({ next }) {
      const unsubscribe = store.subscribe(() => next(store.getState()))
      next(store.getState())
      return { unsubscribe }
    }
  }
}
```

Similarly, you can compose different asynchronous streams to turn them into actions before feeding them to `store.dispatch()`.

The question is: do you really need Redux if you already use Rx? Maybe not. It's not hard to [re-implement Redux in Rx](https://github.com/jas-chen/rx-redux). Some say it's a two-liner using Rx `.scan()` method. It may very well be!

If you're in doubt, check out the Redux source code (there isn't much going on there), as well as its ecosystem (for example, [the developer tools](https://github.com/gaearon/redux-devtools)). If you don't care too much about it and want to go with the reactive data flow all the way, you might want to explore something like [Cycle](http://cycle.js.org) instead, or even combine it with Redux. Let us know how it goes!
