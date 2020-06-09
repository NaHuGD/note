# React Hook
## 使用 State Hook (useState)
-  State Hook取代class寫法
```js
// 舊版class寫法
class Hook extends React.Component {
    constructor(){
        super()
        this.state = {
            count: 0
        }
    }

    render() {
        return (
            <div>
                <h1>點擊次數{this.state.count}</h1>      
                <button onClick={() => this.setState({
                    count: this.state.count + 1
                })}>點我</button>  
            </div>
        )
    }
}
```
- 使用React中的useState
```js
import React,{ useState } from 'react'

const Hook = () =>{
    // 這邊定義一個變數count = 0,useState(0)為一開始count中的值
    // setCount為可以調用count更動的值
    const [count, setCont] = useState(0);
    
    return(
        <div>
            <h1>點擊次數{count}下</h1>
            {/* 使用者點擊呼叫setCount傳入新的值 */}
            <button onClick={() => setCont(count + 1)}>點擊</button>  
        </div>
    )
}
```
- 可以使用function或是class
```js
const Example = (props) => {
  // 你可以在這裡使用 Hook！
  return <div />;
}
```
```js
function Example(props) {
  // 你可以在這裡使用 Hook！
  return <div />;
}
```
- ### 使用setSomething(setCount)會將舊有的資料刪除,如果重複使用更新同一筆資料,需用解構帶入原本的資料
```js
const [count, setCount] = useState()
setCount((preveState) => ({
    ...preveState,
    '更新資料'
}))
```
## 什麼是 Hook？
- Hook是react中的特殊function
- useState 是一個讓你增加 React state 到 function component 的 Hook

## 使用 Effect Hook (useEffect)
- 可以把useEffect視為React class生命週期方法(componentDidMount, componentDidUpdata, componentWillUnmount)的組合
- 可以帶入兩個參數
```js
useEffect(() => {
    '要更新的資料'
},[dependencies])
```
- 第二個參數 dependencies 是一個陣列[] 避免無限迴圈,只要重新渲染後dependencies內元素沒有改變,useEffect裡的函示就不會執行
```js

```

## useCallback
- ( 用來將函示保存下來 ),不會隨著組件重新執行,得到兩個不同的函式
- useCallback的用法和useEffect一樣,可帶入兩個參數
  - 參數一是一個韓式
  - 參數二是 dependencies 
```js
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```
- 使用在需複用在useEffect中的函式

## useMemo 
- 類似useCallback
- 在dependencies沒有改動的情況下,將return的值保存下來

## useContext
- 類似redux簡化版的資料傳遞
```js
const stateContext = React.createContext()
const getContextValue = () => {
    return{
        state: 1
    }
}
// 包覆在最上層,並將資料透過value傳遞
<stateContext.Provider value={getContextValue()} >
    <App />
</stateContext.Provider >
```
子層調用
```js
// App
import React, { useContext } from 'react'
const App = () => {
    const stateContext = React.createContext()
    const context = useContext(stateContext)
    return(
        <h1>{context.state}</h1> // 1
    )
}
```