# Hook
## Hook을 사용하는 이유

React에는 Function component와 class component가 있음


### Function 컴포넌트와 Class 컴포넌트의 차이점
|Function component|Class Component|
|------|---|
|- state 사용 불가|- 생성자에서 state를 정의|
|- Lifecycle에 따른 기능 불가|- setState()함수를 통해 state 업데이트|
|| lifecycle methods 제공|

함수 컴포넌트는 간결함, state 사용할 수 없다는 특징이 있음
-> 이러한 기능을 보완하기 위해서 `hook`을 사용함

## Hook
원래 존재하는 기능에 추가적인 기능을 갈고리처럼 추가한다는 의미
- state 관련 함수
- lifecycle 관련 함수
- 최적화 관련 함수

----
[1. useState](http://www.google.co.kr)
[2. useEffect](http://www.google.co.kr)
