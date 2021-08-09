## document Object Model

在 JavaScript 裡面，想要控制 HTML elements 的話，我們可以操作 DOM 來實現，因為每個 html element 都是一個物件，裡面已經有可以用的 properties 跟 methods。

### Document Object

#### methods

- addEventListener()
- createElement()
- getElementById()
- getElementsByClassName()
- querySelector()
- querySelectorAll()

NodeList 很像 Array，但它不是 Array。
如果是 Array 的話，它會有 Array 的方法，例如 pop()

---

<!-- 下面這一段是在講function -->

## Arrow Function Expression

function declaration

```js
function sayHi() {
  console.log('Hi!')
}
```

arrow function expression

```js
const sayHi = () => {
  console.log('Hi!')
}
```

### Hoisting

function 在宣告之前使用，會有 Hoisting

```js
sayHi() // Hi!

function sayHi() {
  console.log('Hi!')
}
```

function 在建立之前使用，會報錯

```js
sayHi() // Uncaught ReferenceError: Cannot access 'sayHi' before initialization

const sayHi = () => {
  console.log('Hi!')
}
```

### this keyword

- "this" means "this object" in function declaration
- "this" means "window object" in arrow function expression
  建議在 Object 裡面的 function 都用 function declaration，這樣才取得到 object 本身的資料。
  使用 Vue 的話會透過 arrow function 搭配 this 來取得 Vue 裡面的資料。

```js
let Apple = {
  name: 'Good apple',
  price: 30,
  // function declaration
  sayPrice() {
    console.log(this.price)
  },
  // arrow function expression
  howMuch: () => {
    // this.price not is Fruit.price, cause this in arrow function
    console.log(this.price)
  },
}

Apple.sayPrice() // 30
Apple.howMuch() // undefined
```


## forEach function
為每一個元素做事。
- forEach is an array property
- forEach function takes one parameter - function (forEach 要傳入帶一個參數的 function)
- the parameter of forEach function is called "CallBack" function (這個傳入的參數叫做 CallBack function)
#### syntax
- 基本語法
```js
let numbers = [7, 13, 25, 36, 47, 5, 88, 49]

function checkNum(n){
  if(n >20) {
    console.log(n)
  }
}

numbers.forEach(checkNum)
```

- loop through an array has two ways, for loop and forEach function (兩種方式去 loop Array, for loop 跟 forEach function)
兩者都可以用，但實務上用forEach居多，forEach可以一眼就看出來是在對numbers這個陣列做事，for loop的話還要花更多時間理解。
```js
let numbers = [7, 13, 25, 36, 47, 5, 88, 49]

// forEach
numbers.forEach(function checkNum(n){
  if(n >20) {
    console.log(n)
  }
})

// for loop
for(let i = 0;i<numbers.length;i++){
  if(numbers[i] > 20) {
    console.log(numbers[i])
  }
}

```

- anonymous function 匿名函式
是指沒有function Name的function，在forEach()裡的function就是一個匿名函式。
  - anonymous function is a type of function declaration (它也是一種 function declaration)
```js
let numbers = [7, 13, 25, 36, 47, 5, 88, 49]

// forEach
numbers.forEach(function(n){
  if(n >20) {
    console.log(n)
  }
})
```

- arrow function expression
```js
let numbers = [7, 13, 25, 36, 47, 5, 88, 49]

// forEach
numbers.forEach((n)=>{
  if(n > 20){
    console.log(n)
  }
})
```

#### parameter
在callback function 裡面要帶的參數
- currentValue 當前的值
- index 索引(可不用)
- array 陣列(可不用)

---
## Array, HTMLCollection and NodeList
- 這三個很相似(都有length跟index)
- HTMLCollection, NodeList
  - 都有 length 這個 property
  - 都有 indices (index的複數)
```js
// array
let numbers = [4,62,30,24]

// HTMLCollection
let containerElements = document.getElementByClassName('container')

// NodeList
let containerSelector = document.querySelectorAll(".container")
```

- array, NodeList可以用forEach()，但HTMLCollection不行
開發上偏好使用`querySelectorAll()`，原因是它可以用forEach()

---
## Element Object
這裡指的是HTML Element
1. 不同的HTML element "可能" 有它自己的方法(methods)跟屬性(properties)，例如`<video>`、`<p>`
2. 所有的HTML element一定會有的properties跟methods 如下
  - addEventListener()
  - appendChild()
  - children
  - childNode
  - classList(add(), remove(), toggle(), contains())
  - getAttribute()
  - innerHTML, innerText
  - parentElement()
  - querySelector()
  - querySelectorAll()
  - remove()

### children and childNode Property
* children returns HTMLCollection
* childNode returns NodeList

### parentElement
* parentElement returns HTMLElement

### innerHTML, innerText
功能上類似，唯一的不同是在於，innerHTML裡面如果含有HTML tag的字串，就會被當作HTML來閱讀，而innerText無論輸入什麼內容，都是當成文字來閱讀。

```js
let h1 = document.querySelector("h1.myh1");
// 畫面顯示為 <mark>Hey apple.</mark>
h1.innerText = "<mark>Hey apple.</mark>";

// 畫面顯示為黃底的 Hey apple.
h1.innerHTML = "<mark>Hey apple.</mark>";
```

### appendChild()
加一個HTMLElement到指定的HTMLElement裡面
```js
// 在body裡面放入一個h1標籤
let body = document.querySelector("body");

let myh1 = document.createElement("h1");
myh1.innerText = "Hey apple";

body.appendChild(myh1)
```

### classList
- 是一個object，有自己的methods跟properties(add(), remove(), toggle(), contains())
- 它會把HTMLElement裡面的class全部回傳回來。

### getAttribute()
- 可以找到HTMLElement已設定的屬性。