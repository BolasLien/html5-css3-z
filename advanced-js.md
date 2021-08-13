# Advanced JavaScript

## array concat method

如何把兩個 Array 串在一起？

### 錯誤的做法

用 `+` 會把兩個陣列轉為字串，合併為一個字串。

```js
let friend1 = ['Mike', 'Josh', 'Doug']
let friend2 = ['Jim', 'David', 'Ben']

let friends = friend1 + friend2
console.log(friends) // Mike,Josh,DougJim,David,Ben
```

### Array.concat()

`Array.concat()` 是連接其它陣列的方法。

```js
let friend1 = ['Mike', 'Josh', 'Doug']
let friend2 = ['Jim', 'David', 'Ben']

let friends = friend1.concat(friend2)
console.log(friends) // ["Mike", "Josh", "Doug", "Jim", "David", "Ben"]
```

### Array Concat with spread
用展開運算子 `...`

```js
let friend1 = ['Mike', 'Josh', 'Doug']
let friend2 = ['Jim', 'David', 'Ben']

let friends = [...friend1,...friend2]
console.log(friends) // ["Mike", "Josh", "Doug", "Jim", "David", "Ben"]
```

---

## NaN and Infinity

JavaScript 中兩個特別的`數字`：`NaN`、`Infinity`

- NaN is a Number (data type). NaN 是 Not a Number 的意思
- Infinity is a Number (data type). Infinity 是無線大的意思
- NaN 會出現在我們把`數字跟字串做數學運算`的時候，或是其它奇怪的事情上。

### isNaN()

要確認一個值是不是 NaN，不能用 `==` 或 `===`，必須用 `isNaN()`。

NaN 代表了`不知道是甚麼數字`概念，有可能是我們把`數字跟字串做數學運算`，也有可能是我們把`Infinity / 0`，也可以說`NaN不代表任何數`，所以 NaN 也不會等於自己。

[這篇很詳細的解釋了 NaN](https://ithelp.ithome.com.tw/articles/10251553)

---

## Spread Operator and Rest Parameters

- `...` is spread operator `...` 是 展開運算子
- rest parameters 其餘參數

### rest parameters

表示不確定數量的參數。

可以在 call function 時傳入不確定數量的參數。

```js
// 傳6個數字
console.log(Math.max(7, 8, 12, -5, 20, 333)) // 333

// 傳3個數字
console.log(Math.max(7, 8, 12)) // 12
```

搭配`...`展開運算子來設計 rest parameter(其餘參數)，其中`numbers`會被視為一個陣列。

```js
function maxNumber(...numbers) {
  let biggest = -Infinity
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] > biggest) {
      biggest = numbers[i]
    }
  }

  return biggest
}

console.log(maxNumber(7, 8, 12, -5, 20, 333)) // 333
```

[其餘參數](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/rest_parameters)
[展開運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

---

## Primitive and Reference
- Primitive Data Types
Number,String,null,undefined等等的Primitive Data Types，它們並不是objects，所以它們沒有自己的properties跟methods (string.length表示...???)

它們的變數存的是value，在記憶體中各自擁有自己的值。
```js
let num1 = 100
let num2 = num1 // num2 複製 num1 的值

num1 = 50

console.log(num1,num2) // 50, 100
```
- Reference Data Types
objects 和 arrays 是 Reference Data Type

它們的變數存的是 non-primitive value，也就是指向記憶體中的某個位址的值，並不是真的擁有自己的值。
```js
let friend1 = ["Amy","Shawn"]
let friend2 = friend1 // friend2 參考 friend1 的位址

friend1.push("David")

console.log(friend1,friend2) // ["Amy", "Shawn", "David"],["Amy", "Shawn", "David"]
```

