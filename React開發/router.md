# react_router路由配置
電腦需先安裝create-react-app
```
npm install -g create-react-app
或用 yarn 命令安裝
yarn global create-react-app
```
在使用create-react-app快速建立專案
```
create-react-app 檔名
```
### 並載入 react_router 至 node_modules (安裝至全域,需到packjson中查看是否有安裝)
```
npm install -g react-router-dom
或
yarn add react-router-dom
```
路由配置方法
```js
import React from 'react'
// BrowserRouter瀏覽器的router
import { BrowserRouter as Router, Route , Link } from 'react-router-dom'

const Index = () => <h2>Home</h2>
const About = () => <h2>About</h2>
const Users = () => <h2>Users</h2>

const AppRouter = ()=>{

}
// 導出組件其他地方才可以引入
export default AppRouter
```