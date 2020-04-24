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
宣告一個const useStyles並將css樣是放入<br>
且在需要調用的函示中加入const classes = useStyles();
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

```js
import Grid from '@material-ui/core/Grid'
import Button from '@material-ui/core/Button'

const useStyles = makeStyles(theme => ({
box: {
  marginTop: theme.typography.pxToRem(22),
  width: '100%',
  height: 'auto',
  borderRadius: theme.shape.borderRadius,
  overflow: 'hidden',
  background: theme.palette.common.white,
},
boxLeft: {
  padding: `${theme.typography.pxToRem(20)} 0`,
},
textAlignCenter: {
  textAlign: 'center',
},
radiusIcon: {
  width: '2.3rem',
  height: '2.3rem',
  display: 'inline-block',
  background: '#49aee1',
  color: theme.palette.common.white,
  borderRadius: '999%',
  border: '.3rem solid #0855a2',
  fontSize: '1.5rem',
  lineHeight: '1.8rem',
},
textTitle: {
  marginTop: theme.typography.pxToRem(15),
  fontSize: '1.1rem',
  display: 'block',
  textAlign: 'center',
  fontWeight: 'bold',
},
textInfo: {
  fontSize: '.8rem',
  display: 'block',
  textAlign: 'center',
  color: '#848383',
},
buttonStyle: {
  margin: `${theme.typography.pxToRem(25)} auto 0 auto`,
  padding: `${theme.typography.pxToRem(5)} ${theme.typography.pxToRem(25)}`,
  display: 'block',
  borderRadius: '1.5rem',
  background: 'linear-gradient(to right, #69b3f8, #4668d1)',
  color: theme.palette.common.white,
  letterSpacing: '.1rem',
},
boxRight: {
  background: 'linear-gradient(135deg, #1563ad 30%, #5eabde)',
},
}))

return(
  <Grid container className={classes.box}>
    <Grid item xs={6} className={classes.boxLeft}>
      <div className={classes.textAlignCenter}>
        <span className={classes.radiusIcon}>N</span>
      </div>
      <span className={classes.textTitle}>意xxxx斯</span>
      <span className={classes.textInfo}>獨家合作夥伴</span>
      <Button variant="contained" className={classes.buttonStyle} onClick={goSponsorInnerPage(1)}>
        查看詳情
      </Button>
    </Grid>
    <Grid item xs={6} className={classes.boxRight}></Grid>
  </Grid>
)
```
可以透過以下方法操控子元件的CSS樣式
```js

const useStyles = makeStyles(theme => ({
  box: {
    '& div':{
      background: 'black',
    }
  },
}))

return(
  <div className={classes.box}>
    <div>背景黑色</div> 
  </div> 
)

```
