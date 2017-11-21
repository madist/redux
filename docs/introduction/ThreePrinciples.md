# 원칙 세가지

Redux 는 세가지 기본원칙으로 설명 될 수 있습니다.

### 단하나의 진실

**앱의 전체 [상태](../Glossary.md#state)는 하나의 [저장소](../Glossary.md#store)** 에 저장됩니다.

따라서 서버의 상태를 별도의 코딩 작업없이 클라이언트에 직렬화하고 접목 시킬 수 있으므로 보편적 인 응용 프로그램을 쉽게 만들 수 있습니다. 단일 상태 트리를 사용하면 응용 프로그램을 디버그하거나 검사하기가 더 쉽습니다. 또한 개발주기를 단축하기 위해 앱 상태를 개발 중에 유지할 수 있습니다. 모든 상태가 단일 트리에 저장되어 있다면 기존에 구현하기 어려운 일부 기능 (예 : 실행 취소 / 다시 실행)을 구현할 수 있습니다.

```js
console.log(store.getState())

/* Prints
{
  visibilityFilter: 'SHOW_ALL',
  todos: [
    {
      text: 'Consider using Redux',
      completed: true,
    },
    {
      text: 'Keep all state in a single tree',
      completed: false
    }
  ]
}
*/
```

### `state(상태)`는 읽기 전용입니다.

**`state(상태)`를 바꾸는 유일한 방법은 [action](../Glossary.md#action) 을 발생시키는 것입니다.**

이렇게 하면 view 혹은 네트워크 콜백이 `state`에 직접 쓸 수 없습니다. 대신, 그들은 `action`을통해 변화될 `state`를 표현합니다. 모든 변경 사항은 중앙 집중식으로 엄격한 순서로 하나씩 발생합니다. 그러므로, 조심해야 할 미묘한 경쟁조건(race condition)이 없습니다. 동작은 단순한 객체이므로 디버깅 또는 테스트 목적으로 기록, 직렬화, 저장 및 나중에 재생할 수 있습니다.

```js
// dispatch(action)

store.dispatch({
  type: 'COMPLETE_TODO',
  index: 1
})

store.dispatch({
  type: 'SET_VISIBILITY_FILTER',
  filter: 'SHOW_COMPLETED'
})
```

### 순수함수를 통해서 변경됩니다.

**액션에 의해 상태 트리가 변환되는 방법을 지정하려면, 순수 [reducers](../Glossary.md#reducer)를 작성해야 합니다.**

`reducer`는 이전 상태와 동작을 취한 순수 상태 함수입니다. 또한, 이전 상태와 동작을 통해서 다음 상태를 반환합니다. 그러나, 이전 상태를 변경하는 것이 아니라 새 상태 객체를 반환하는 것임을 잊지 마십시오. 하나의 `reducer`로 시작할 수 있으며 앱이 커짐에 따라 상태 트리의 특정 부분을 관리하는 더 작은 `reducer`로 분할 할 수 있습니다. 감속기는 단지 함수이기 때문에 호출 순서를 제어하거나, 추가 데이터를 전달하거나, 페이지처리와 같은 일반적인 작업을 위해 재사용 가능한 `reducer`를 만들 수도 있습니다.

```js
function visibilityFilter(state = 'SHOW_ALL', action) {
  switch (action.type) {
    case 'SET_VISIBILITY_FILTER':
      return action.filter
    default:
      return state
  }
}

function todos(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return [
        ...state,
        {
          text: action.text,
          completed: false
        }
      ]
    case 'COMPLETE_TODO':
      return state.map((todo, index) => {
        if (index === action.index) {
          return Object.assign({}, todo, {
            completed: true
          })
        }
        return todo
      })
    default:
      return state
  }
}

import { combineReducers, createStore } from 'redux'
const reducer = combineReducers({ visibilityFilter, todos })
const store = createStore(reducer)
```

이게 전부다! 이제 여러분은 Redux가 무엇에 관한건지 알 수 있습니다.