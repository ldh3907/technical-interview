# technical-interview

기술 면접을 대비하기 위해 면접 질문들을 리스트업 해보려고 합니다.<br>
내용에 대해 잘못된 부분이나, 오타가 있으면 `PR` 부탁드립니다.

1. 스코프란?

   - 변수에 접근할 수 있는 범위이며, 전역스코프와 지역스코프 두가지가 있다.
   - 전역 스코프는 어느 곳에서든 참조할 수 있고, 지역 스코프는 생성된 범위 내에서만 참조 할 수 있다.
   - 보통 언어에서 지역 스코프는 블록 레벨 스코프 `if{...} ..` 를 따르지만 자바스크립트는 함수 레벨 스코프를 따른다. `function() {}`
   - 참조해야하는 변수가 있는데 형성된 스코프내에 없으면 상위 스코프에서 찾게 되는데 이를 스코프 체이닝이라고 한다.
   - 스코프는 함수가 실행될 때가 아닌 선언될 때 만들어진다.

2. window.setTimeout(() => {}, 0)을 했을때 일어나는 일

   - 먼저 setTimeout 함수를 실행하게 되면 Web API에 있는 Timeout이 실행된다. Web API가 Timeout을 실행하고 0초를 기다린 후에, 받은 콜백함수를 Callback Queue에 넣는다. 마지막으로 이벤트루프가 Call Stack과 Callback Queue를 확인하면서 Call Stack이 비었을 때 Callback Queue에 들어갔던 콜백함수를 Call Stack에 넣고 콜백함수가 실행이된다.
   - 사실 0초를 기다리지는 않는다. delay 최소값은 브라우저가 결정한다. 원래 브라우저는 최소값을 10ms로 지정하지만 최신 브라우저에서는 4ms로 지정한다.

3. 호이스팅이란?

   - 먼저 호이스팅은 변수들을 참조하기 위해서 변수들을 모아 최상단으로 끌어올려 초기화 하는 과정을 말한다.
   - 자바스크립트가 처음 실행될 때 전역 컨텍스트가 생성되면서 전역 렉시컬 환경의 환경레코드가 `let`, `const`, `var`, `function`, `=`으로 선언된 함수, 변수 등을 수집한다. 이 때 수집하면서 초기화 하는 과정에서 최상단으로 끌어올려지게 된다.
   - var 키워드로 선언된 변수는 호이스팅 과정에서 undefined로 초기화 된다. 그래서 변수가 선언되기전에 참조가 가능하다.
   - let, const 키워드로 선언된 변수는 호이스팅 과정에서 &lt;uninitialized&gt; 로 초기화 된다. 저 uninitialized는 참조할 수 없는 값이다. 그래서 let, const로 선언된 변수는 선언전에 참조하게 되면 참조에러가 나게 된다.

4. 내부슬롯, 프로퍼티 어트리뷰트란?

   - 먼저 내부슬롯은 [[Prototype]] 같이 자바스크립트 내부 동작에 사용되는 값이다.
   - 내부 동작에서 사용되기 때문에 개발자가 직접적인 호출을 하지 못한다. 하지만 간접적으로 접근할 수 있도록 접근할 수 있도록 `Object.getOwnPropertyDescriptor()`등 과 같은 메소드를 제공한다.
   - 내부슬롯 중 [[Environment]]라는 프로퍼티가 있는데, 이는 위에서 설명했던 스코프체이닝에 필요한 외부 렉시컬 환경 정보가 담기는 곳이다.
