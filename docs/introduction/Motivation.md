# 개발동기

JavaScript 단일 페이지 응용 프로그램(SPA)에 대한 요구 사항이 점차 복잡해지면서 **`우리 코드는 이전보다 더 많은 상태를 관리해야합니다`** . 이 상태에는 아직 서버에 저장되지 않은 로컬로 생성 된 데이터뿐만 아니라 서버 응답 및 캐시 된 데이터가 포함될 수 있습니다. 활성 상태의 경로, 선택된 탭, 로딩 인디케이터, 페이징 컨트롤러등을 관리해야 하기 때문에 `UI 상태`도 복잡해지고 있습니다.

이 끊임없이 변화하는 상태를 관리하는 것은 어렵습니다. 모델이 다른 모델을 업데이트 할 수있는 경우 뷰는 다른 모델을 업데이트하는 모델을 업데이트 할 수 있으며, 그러면 다른 뷰가 업데이트 될 수 있습니다. 어떤 시점에서, 당신은 더 이상 당신의 앱이 **`언제,어떻게 그리고 어떻게 그 상태를 제어 할 수 없었는지 이해하지 못합니다`** 시스템이 불투명하고 비 결정적 일 때는 버그를 재현하거나 새로운 기능을 추가하기 어렵습니다.

만일, 이게 그렇게 나쁘게 느껴지지 않는다면, **`프론트 엔드 제품 개발에서 새로운 요구사항이 늘어난다는 것을`** 생각해보세요. 개발자는 최적화된 업데이트, 서버 렌더링, 경로 전환을 수행하기 전에 데이터 가져오기 등을 처리해야합니다. 우리는 전에 결코 다룰 수 없었던 복잡성을 관리하려고 노력하고 있으며 필연적으로 다음과 같은 질문을합니다. [포기할 때가 되었습니까?](http://www.quirksmode.org/blog/archives/2015/07/stop_pushing_th.html) `대답은 _no_입니다.`

이 복잡성은 다루기가 힘듭니다 **`인간이 추론하기에 매우 어려운 두 가지 개념(상태변화와 비동기)을 함께 사용하기 때문입니다.`** 나는 그들을 [Mentos and Coke](https://en.wikipedia.org/wiki/Diet_Coke_and_Mentos_eruption). 이 둘은 나누어 보면 훌륭하지만, 함께하면 엉망이됩니다. [React](http://facebook.github.io/react)와 같은 라이브러리는 비동기 및 직접 DOM 조작을 제거하여 뷰 계층에서이 문제를 해결하려고 시도합니다. 그러나 데이터 상태를 관리하는 것은 여러분의 몫이며 이 부분이 `Redux`가 해결할 부분입니다.

Following in the steps of [Flux](http://facebook.github.io/flux), [CQRS](http://martinfowler.com/bliki/CQRS.html), and [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html), **Redux attempts to make state mutations predictable** by imposing certain restrictions on how and when updates can happen. These restrictions are reflected in the [three principles](ThreePrinciples.md) of Redux.
