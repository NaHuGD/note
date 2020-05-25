# TypeScript
### 使用typescript必須在每個變數後面定義它的型別
- boolean
```ts
const isDone: boolean = false
```
- number
```ts
const isNum: number = 12345
let listArray: number[] = [1, 2, 3]
```
- string
```ts
const isStr: string = '哈囉'
```
- void 用在沒有任何返回值時
  - 賦予void的型別,不能在賦予值,但賦予undefined和null的型別可以
```ts
function isFn():void{
    console.log('void')
}

let  unusable:void = null
```
- readonly 只讀屬性,只能在第一次的時候賦予值
```ts
interface Point {
    readonly id:number
}
let arr:Point ={
    id:30
}
// 以下會報錯
arr.id = 87
```
## TypeScript中的型別推論
- TypeScript會在沒有明確的型別時,推測出一個型別
<p>以下程式碼myFavoriteNumber變數會被推斷為string型別</p>

```ts
let myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
```
會變成
```ts
let myFavoriteNumber:string = 'seven';
myFavoriteNumber = 7;
```
如果定義變數時沒有賦予值,則都會被推斷成any
```ts
let myFavoriteNumber; //(any)
myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
```
## 聯合型別
- 使用 | 分隔每個型別
- 表示值可以為多種型別
```ts
let myFavoriteNumber: string | number;
myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
```
## 物件型別-介面
- 在TypeScript中可以使用 interface 來定義物件型別
- 介面一般首字母大寫。有的程式語言中會建議介面的名稱加上 I 字首。
```ts
interface IProps {
    name: string
    type: number
}
let arr: IProps = {
    name: 'IAN',
    type: 0
}
```



