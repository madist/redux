# 핵심 개녕

Redux 자체는 매우 간단합니다.

앱의 상태가 평범한 객체로 묘사 된 것을 상상해보십시오. 예를 들어 수행 할 앱의 상태는 다음과 같습니다.

```js
{
  todos: [{
    text: 'Eat food',
    completed: true
  }, {
    text: 'Exercise',
    completed: false
  }],
  visibilityFilter: 'SHOW_COMPLETED'
}
```

이 객체는 setter가 없다는 점을 제외하면 "모델"과 같습니다. 이는 코드의 다른 부분이 상태를 임의로 변경할 수 없기 때문에 재현하기 어려운 버그가 발생합니다.

상태를 바꾸려면 `action`을 `dispatch`해야합니다. `action`은 일어난 일을 설명하는 일반 JavaScript 객체입니다 (이것은 마법이 아닙니다). 다음은 몇 가지 예시 작업입니다.

```js
{ type: 'ADD_TODO', text: 'Go to swimming pool' }
{ type: 'TOGGLE_TODO', index: 1 }
{ type: 'SET_VISIBILITY_FILTER', filter: 'SHOW_ALL' }
```

모든 변경 사항을 액션으로 설명하면 앱에서 어떤 일이 벌어지고 있는지 명확하게 알 수 있습니다. 무언가가 변경되면 왜 변경되었는지 알 수 있습니다. 행동은 무슨 일이 일어 났는지 빵 부스러기와 같습니다.

마지막으로 `state`와 `action`을 연결하기 위해 `reducer`라는 함수를 작성합니다. 다시 말하지만, 여기에는 마법은 없습니다. 그것은 `state`와 `action`을 인수로 취하고 함수의 다음 상태를 반환하는 함수입니다.

큰 응용 프로그램을 위해 그런 함수를 작성하는 것은 어려울 것입니다. 그래서 우리는 상태의 일부를 관리하는 더 작은 함수를 작성합니다 :

```js
function visibilityFilter(state = 'SHOW_ALL', action) {
  if (action.type === 'SET_VISIBILITY_FILTER') {
    return action.filter
  } else {
    return state
  }
}

function todos(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return state.concat([{ text: action.text, completed: false }])
    case 'TOGGLE_TODO':
      return state.map(
        (todo, index) =>
          action.index === index
            ? { text: todo.text, completed: !todo.completed }
            : todo
      )
    default:
      return state
  }
}
```

그리고 우리는 두 개의 `reducer` 해당 상태 키로 호출하여 앱의 전체 상태를 관리하는 또 다른 `reducer`를 작성합니다.

```js
function todoApp(state = {}, action) {
  return {
    todos: todos(state.todos, action),
    visibilityFilter: visibilityFilter(state.visibilityFilter, action)
  }
}
```

이것은 기본적으로 Redux의 전체 아이디어입니다. Redux API는 사용하지 않았습니다. 이 패턴을 용이하게하는 몇 가지 유틸리티가 있지만 주요 아이디어는 액션 객체에 대한 응답으로 상태가 어떻게 업데이트되는지를 설명하고 작성한 코드의 90 %는 Redux를 사용하지 않는 단순한 JavaScript입니다. 이것이 자체 API 이고 여러분이 생각하는 마술입니다.