# Redux說明
- 所有資料(state)只存在唯一一個store中
- 唯一改變state方法是透過觸發action
    - redux定義好內部資料,外部須變更透過store.dispatch觸發對應消息
## Action
- action是把數據傳到store的有效載荷(paylod) 
- action為綁定好的事件名稱,用dispatch觸發
```js
import {createStore} from 'redux'
// reducer
function counter(state = 0, action){
    switch(action.type){
        case 'add':
            return state + 1
        case 'less':
            return state - 1
        default:
            return state
    }
}

const store = createStore(counter)
const action = {type:'add'} // +1
store.dispatch(action) // 1
```

## Reducer
- reducer指定資料狀態變化後如何響應action,並發送到store
- subscribe監聽
```js
// state值有變化時就會觸發function
store.subscribe(function(){
    console.log('監聽state',store.getState() )
})
```

## store
- 掌管應用程式狀態
- 允許透過getState()取得資料狀態
- 允許透過dispatch(action)更新state

### combineReducers(合併reducer功能)
```js
const { createStore,combineReducers } = Redux;

const store = createStore(combineReducers({
    counter,
    user
}));
// 使用combineReducers時原本值會變物件,所以必須在指定其位置
store.getState().counter
```
搭配combineReducers操作多個reducer
```js
// reducer
function counter(state = 0, action) {
    switch (action.type) {
        case 'add':
            return state + 1;
        case 'less':
            return state - 1;
        default:
            return state
    }
}
function user(state = '無名', action) {
    switch (action.type) {
        case 'set':
            return action.name
        default:
            return state
    }
}
//
const store = createStore(combineReducers({
    counter,
    user
}));
// store.getState().counter //-1
store.dispatch({ type: 'less' }) 
// store.getState().user //瘦虎 
store.dispatch({
    type: 'set',
    name: '瘦虎'
})
```
- ### 使用combineReducers合併reducers時,他會將reducer中的陣列{}解開,所以reducer回傳時不用再回傳物件
```js
case "TEST": {
    return {
        ...state,
        receiptType: action.receiptType
    }
}
```

# 搭配react,react redux
- ### Provider
  - store需藉由Provider傳遞,Provider須包在最外層
```js
// imdex.js
import { Provider } from 'react-redux'

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```
- ### connect
  - 內部元件需使用connect取得Provider傳遞的參數
```js
import { connect } from 'react-redux'
const App = () => {
    ....
}
// connect和App進行連結
export default connect()(App)
```
- connect可以帶入兩個參數(mapStateToProps, mapDispatchToProps)
- mapStateToProps可以取得reducer時的state值
```js
import { connect } from 'react-redux'
const App = () => {
    render = () => {
        return(
            // reducer宣告的state值ㄌ
            <h1>{this.props.num}</h1>
        )
    }
}

const mapStateToProps = (state) => {
    return (
        num: state
    )
}

export default connect(mapStateToProps)(App)
```
## mapStateToProps
- mapStateToProps負責建立組件store跟state的映射關係 (連結資料)
## mapDispatchToProps
- mapDispatchProps定義組件如何發出store.dispatch(action) (連結事件)
## 封裝/分離react redux
- 將redux會用到的資料另開到store資料夾下
```js
// store/index.js
// 專門放store檔
import { createStore } from 'redux'
import reducers from './reducers'

const store = createStore(reducers)
store.subscribe(() => {
    console.log('有更新', store.getState())
})

export default store
```

```js
// reducers/index.js
// 統整放reducers
import counter from './counter'
import user from './user'
import { combineReducers } from 'redux'
// 用combineReducers合併counter,user檔
export default combineReducers({
    counter: counter,
    user: user
})
```

```js
// reducer/counter.js
// reducer
const counter = (state = 1, action) => {
    switch (action.type) {
        case 'add':
            return state + 1
        default:
            return state
    }
}
export default counter
```
```js
// reducer/user.js
// reducer
const user = (state = '未知', action) => {
    switch (action.type) {
        case 'set':
            return action.name
        default:
            return state
    }
}

export default user
```

