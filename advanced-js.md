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

let friends = [...friend1, ...friend2]
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
  Number,String,null,undefined 等等的 Primitive Data Types，它們並不是 objects，所以它們沒有自己的 properties 跟 methods (string.length 表示...???)

它們的變數存的是 value，在記憶體中各自擁有自己的值。

```js
let num1 = 100
let num2 = num1 // num2 複製 num1 的值

num1 = 50

console.log(num1, num2) // 50, 100
```

- Reference Data Types
  objects 和 arrays 是 Reference Data Type

它們的變數存的是 non-primitive value，也就是指向記憶體中的某個位址的值，並不是真的擁有自己的值。

```js
let friend1 = ['Amy', 'Shawn']
let friend2 = friend1 // friend2 參考 friend1 的位址

friend1.push('David')

console.log(friend1, friend2) // ["Amy", "Shawn", "David"],["Amy", "Shawn", "David"]
```

## primitive coercion

### Why do primitive still own properties and methods?

為什麼 Primitive 還是會有 properties 跟 methods?

#### JavaScript has a property call "coercion"

coercion (n.) 強制

在使用 Primitive data type 的時候，如果沒對它做任何事情，那它就是 primitive data type。

但是如果使用了 property 或 methods，JavaScript 會做 coercion，把 primitive data type 強制轉為 object 來執行。

```js
// string primitive data type
let name = 'JavaScript'

// 使用 .toLowerCase() 會轉型為 String object
console.log(name.toLowerCase())
```

#### primitive data type v.s object

以字串來說，如果想要的話，也可以用 `new String()` 來建立 string object。

**但是建立 string object，會一起連 properties 跟 methods 都一起建立，導致占用的記憶體效能較大，因此非常不建議這麼做。**

```js
let name1 = 'JavaScript'
let name2 = new String('JavaScript')

// 印出變數
console.log(name1) // JavaScript
console.log(name2) // String {"JavaScript"}

// 檢查type
console.log(typeof name1) // sting
console.log(typeof name2) // object
```

## string comparison

字串拿來比大小

- 會先轉型成數字來做比較，英文字會轉編碼來做比較
- 取第一個字的編碼來做比較

```js
console.log('A' < 'B') // true
console.log('Apple' < 'Banana') // true
console.log('5' > '10') // true
console.log('5' > '49999') // true
```
---
## check if it's an array

如果我們用`typeof`去檢查一個 array，會得到 object，那我們要用甚麼辦法才能知道呢？可以用`Array.isArray()`

```js
let fruits = ['apple', 'banana', 'cherry']

console.log(typeof fruit) // object

console.log(Array.isArray(fruit)) // true
```

## Advanced Array Functions

### map function

建立一個 array，內容是原本陣列執行一個 callback 回傳結果的集合。

也就是說用原本陣列的每個元素，進行運算後，再做成新的 array。

```js
let fruits = ['apple', 'banana', 'cherry']

let upperFruit = fruit.map(item => {
  // 字串轉成大寫
  return item.toUpperCase()
})

console.log(upperFruit) // ["APPLE", "BANANA", "CHERRY"]
```

### find and filter

- find 回傳陣列中符合條件的`第一個元素`，如果沒有任何元素符合的話，就會回傳`undefined`
- filter 回傳陣列中符合條件的`所有元素的集合`，如果沒有任何元素符合的話，就會回傳`空陣列`

```js
let fruits = [
  {name: 'apple', price: 20},
  {name: 'banana', price: 20},
  {name: 'cherry', price: 50},
]

let find20 = fruit.find(fruit => {
  return fruit.price === 20
})

let filter20 = fruit.filter(fruit => {
  return fruit.price === 20
})

console.log(find20) // {name: "apple", price: 20}
console.log(filter20) // [ {name: "apple", price: 20}, {name: "banana", price: 20} ]
```

### some and every

符合條件就回傳 true，否則就回傳 false。

- some 有些(至少有一個)元素符合條件
- every 全部元素符合條件

```js
let fruits = [
  {name: 'apple', price: 20},
  {name: 'banana', price: 20},
  {name: 'cherry', price: 50},
]

let some20 = fruit.some(fruit => {
  return fruit.price === 20
})

let every20 = fruit.every(fruit => {
  return fruit.price === 20
})

console.log(some20) // true
console.log(every20) // false
```

### sort array of strings and numbers

sort 是用來排序 array 內的元素，使用 sort()會改變原本的 array

```js
let fruits = ['Grapes', 'Apple', 'Banana']

fruits.sort()

console.log(fruits) //["Apple", "Banana", "Grapes"]
```

不管是排數字或字串，都會用 string comparison 的方式排，即比對第一位數來排序

```js
let numbers = [12, 43, 36, 99, 17, 1, 4]

numbers.sort()

console.log(numbers) // [1, 12, 17, 36, 4, 43, 99]
```

要避免 string comparison 的排序方式，可以加入 callback 來改變排序方式。

```js
let numbers = [12, 43, 36, 99, 17, 1, 4]

// a - b < 0  =>  a 放前面 b放後面
// a - b = 0  =>  a b 位置不改變
// a - b > 0  =>  a 放後面 b放前面
numbers.sort((a, b) => {
  return a - b
})

console.log(numbers) // [1, 4, 12, 17, 36, 43, 99]
```

sort callback function 應用
如果要照文字長度來排序要怎麼作？

```js
let fruits = ['Grapes', 'Apple', 'watermelon']

fruits.sort((a, b) => {
  return a.length - b.length
})

console.log(fruits) // ["Apple", "Grapes", "watermelon"]
```

---
### for of loop
for...of 的語法會循環`可循環的物件`(iterable objects)的值，找出array的每個元素的value，跟forEach類似。

要注意如果用for...of只能用在iterable objects，如果去跑一般的object會出錯。

iterable objects 如下列
- String
- Array
- array-like objects (例如 NodeList)

```js
let numbers = [10,20,30]
// n 代表的是 numbers 的元素
for(let n of numbers){
  console.log(n)
}
```

### for in loop
for...in 的語法會循環 object `所有可枚舉的屬性`(enumerable properties)，找出object的property name或array的index。

跟for...of不一樣的地方是，for...in可以用在object也可以用在array。