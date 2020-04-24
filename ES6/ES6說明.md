# ES6 const & let
## [ES6入門連結](https://es6.ruanyifeng.com/#docs/let)
## const,let 作用範疇
- 使用let取代var宣告變數
```js
function vatTest(){
  var x = 31;
  if(1){
    var x =71;
    console.log(x); //71
  }
  console.log(x); //71
}
```
使用let的作用範疇在{}內
```js
function vatTest(){
  let x = 31;
  if(1){
    let x =71;
    console.log(x); //71
  }
  console.log(x); //31
}
```
- 使用const宣告常數,常數宣告後就無法改變
  - 宣告後資料不再改變時就可以使用const(常數)
  - 減少變數的濫用
```js
const a = 55;
a = 10; // err
const a = 15; // err
```

# ES6樣板字串
- 使用``符號包覆
- 可有多行文字
- 可使用變數及常數
  - 用$字號,大括號包覆{} 

    ``` js
    const year = new Date().getFullYear();
    const text = `今年是${year}年`
    console.log(text) //"今年是2020年"
    ```
    
# 其餘參數
- 使用...可以將質轉化為參數
 ```js
function sum(...num){
  console.log(num) // [1, 2, 3, 4, 5]
  console.log(...num) // 1 2 3 4 5 
  let total = 0;
  for(let i =0;i < num.length;i++){
    total += num[i];
  }
  return total
}

console.log(sum(1,2,3,4,5))
 ```

# 物件類別與模組

## 物件
- 以大括號{}包住
- 值可給定定任何型態 字串/文字/陣列/物件/函式
```js
const obj ={
 name: 'Ian' //屬性:值 
}
```

