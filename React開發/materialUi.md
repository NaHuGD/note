# Material-UI
### 有點類似bootstrap用法,用來排版
-需先安裝material-ui至專案中
```
// 用npm安装
npm install @material-ui/core

// 用yarn安装
yarn add @material-ui/core
```
自己寫css用法,載入 makeStyles

```
import { makeStyles } from '@material-ui/core';
```
宣告一個const useStyles
```tsx
const useStyles = makeStyles((theme) => ({
  box: {
    background: 'red'
  }
}))

function App() {
  const classes = useStyles();
  return(
    <div className={classes.box}>
    設定className並將其指向useStyles中
    </div>
  )
}
```
