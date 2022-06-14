# useState
state 사용하기 위한 Hook

## useState() 사용법

```javascript
const [변수명, set함수명] = useState(초기값);
```

버튼을 클릭할 때마다 count 수가 증가하는 기능
```js
import React, {useState} from "react";

function Counter(props){
	const[count, setCount] = useState(0);
	
	return(
	<div>
		<p>총 {count}번 클릭했습니다.</p>
		<button onClick={()=> setCount(count+1)}>
			클릭
		</button>
	</div>
);
}
```

input 창에 이름을 입력하고 upload를 하면 화면에 추가되는 기능
```js
import React, {useState, useEffect, useRef} from 'react';

function App(){
  const [names, setNames] = useState(["홍길동", "김민수"]); //name 창에 존재하는 기본 값
  const [input, setInput] = useState(''); //input 창의 기본 값
  const handleInputChange = (e) =>{
    setInput(e.target.value);
  };//현재 value 값으로 input값을 변경해주는 함수

  console.log(input);

  const handleUpload = () =>{
    setNames((prevState)=>{
      return([input, ...prevState])
    })
  }//이전 값과 현재 값을 추가해서 name값을 재설정해줌

  return(
    <div>
      <input type="text" value={input} onChange={handleInputChange}/>
      <button onClick={handleUpload}>Upload</button>
      {names.map((name,idx)=>{
        return <p key={idx}>{name}</p>
      })}
    </div>
  )
}

export default App;
```
<img width="479" alt="스크린샷 2022-06-14 오후 10 33 12" src="https://user-images.githubusercontent.com/78894678/173589793-cc779b3f-043c-4e43-a216-2acbb7997e63.png">

