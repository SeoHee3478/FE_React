#useRef
## 기본 문법 구조
```js
const ref = useRef(value)
```

## useRef를 사용하는 이유
1. 저장공간
state 변화 -> 렌더링 -> 컴포넌트 내부 변수 초기화

But, State 대신 ref안에 저장해놓은다면?!

ref 변화 -> No렌더링 -> 변수 값 유지
state 변화 -> 렌더링 -> 그래도 Ref값은 유지

2. DOM 요소에 접근
input 요소를 클릭하지 않아도 focus를 줄 수 있음

### 저장공간
Ref의 장점
- state는 바뀔 때 마다 계속 렌더링(성능에 안좋은 영향)되지만 ref를 사용하면 아무리 바꿔도 렌더링을 발생시키지 않아 성능이 좋음
```js
import React, {useState, useRef} from 'react';

const App = () => {
  const [count, setCount] = useState(0);
  const countRef = useRef(0);

  
  console.log('렌더링...');

  const increaseCountState = () => {
    setCount(count + 1);
  };

  const increaseCountRef = () =>{
    countRef.current = countRef.current + 1;
    console.log("Ref: ", countRef.current);
  }

  return(
    <div>
      <p>State: {count}</p>
      <p>Ref: {countRef.current}</p>
      <button onClick={increaseCountState}>State 올려</button>
      <button onClick={increaseCountRef}>Ref 올려</button>
    </div>
  );
};

export default App;
```
