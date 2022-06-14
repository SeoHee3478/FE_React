# useEffect()

side effect(효과, 영향)를 수행하기 위한 Hook

→ 다른 컴포넌트에 영향을 미칠 수 있으며, 렌더링 중에는 작업이 완료될 수 없기 때문

→ 리액트의 함수 컴포넌트에서 side effect를 실행할 수 있게 해주는 Hook

useEffect() 사용법
1. 내부에 콜백함수, value 값
```js
useEffect(이펙트 함수, 의존성 배열);
```
의존성 배열: 이 이펙트가 의존하고 있는 변수,
배열안에 있는 변수가 하나라도 바뀌면 재랜더링 됨

처음 컴포넌트가 렌더링된 이후, 재랜더링된 이후에 실행

2. 내부에 콜백함수, 비어있는 value 값
Effect 함수가 mount, unmount시에만 실행되게 하려면 배열 값을 비워주면 된다!
```js
useEffect(이펙트함수, []);
```
-> 1,2번은 매번 렌더링 되는 것이 아니라 화면에 **첫 렌더링** 될 때 실행되고 **배열 내부의 값이 바뀔 때**만 실행된다

3. 내부에 콜백함수만!
의존성 배열을 생략하면 컴포넌트가 업데이트 될 때 마다 호출된다
```js
useEffect(이펙트함수);
```

## 실습
```js
import React, {useState, useEffect} from 'react';


function App2(props) {
    const[count, setCount] = useState(1);
    const[name, setName] = useState('');

    const handleCountUpdate = () => {
        setCount(count + 1);
    }

    const handleInputChange = (e) => {
        setName(e.target.value);
    }

    //렌더링 될 때 마다 매번 실행됨
    useEffect(() => {
        console.log('렌더링');
    })

    //마운팅 + coun가 변화할 때 마다 실행됨
    useEffect(()=>{
        console.log('count 변화');
    },[count])

    //마운팅 + name값이 변화할 때 마다 실행됨
    useEffect(() => {
        console.log('name 변화');
    }, [name])

    return (
        <div>
            <button onClick={handleCountUpdate}>Update</button>
            <span>count: {count}</span>
            <input type="text" value={name} onChange={handleInputChange}/>
    <span>name: {name}</span>
        </div>
    );
}

export default App2;
```
