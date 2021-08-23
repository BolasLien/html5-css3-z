## constructor function
我們可以透過constructor function 來製作大量的 objects。

- constructor是用new來創造物件。
- new出來的物件會繼承object prototype

### constructor 的應用
我們要做出很多「人」，每個人都有自己的名字、年齡、身高、體重。

如果一個一個宣告就要寫很多程式碼
```js
let ming = {
  name:"小明",
  age: 28,
  height: 179,
  weight: 70
}

let hua = {
  name:"小華",
  age: 30,
  height: 169,
  weight: 60
}

let chan = {
  name:"小陳",
  age: 18,
  height: 177,
  weight: 68
}
```

用constructor function的方式我們可先創造「人」這個容器，當我們要添加「小明」，就把「小明」的資料用「人」來裝。
```js
function Person(name, age, height, weight) {
  this.name = name,
  this.age = age,
  this.height = height,
  this.weight = weight
}

let ming = new Person("小明", 28, 179, 70)

console.log(ming)
```

![](./constructor-function.jpg)

### constructor and prototype
人除了基本資料之外，還會有行為，所以也可以定義人有「打招呼」這個行為。
```js
function Person(name, age, height, weight) {
  this.name = name,
  this.age = age,
  this.height = height,
  this.weight = weight
  this.sayHi = function(){
    console.log(this.name + " says hi.")
  }
}

let ming = new Person("小明", 28, 179, 70)

ming.sayHi() // 小明 says hi.
```

new另外一個叫做「小華」的人，會發現一個問題。

小華和小明是不同的兩個人，雖然兩個人都有sayHi()，但是屬於各自物件裡的function，意味著兩個人的sayHi()是不同的。
所以，每new一個新的Person object，就會有新的sayHi()被分配到記憶體裡。如果new了100個人，就會有100個sayHi()。

```js
function Person(name, age, height, weight) {
  this.name = name,
  this.age = age,
  this.height = height,
  this.weight = weight
  this.sayHi = function(){
    console.log(this.name + " says hi.")
  }
}

let ming = new Person("小明", 28, 179, 70)
let hua = new Person("小華", 30, 169, 60)

ming.sayHi() // 小明 says hi.
hua.sayHi() // 小華 says hi.

console.log(ming.sayHi === hua.sayHi) //false
```

我們希望不管new了多少個Person object，大家都會共用同一個sayHi()，這樣就不會浪費記憶體效能。
可以使用prototype來改寫：只要是Person就能有sayHi()的方法。
```js
function Person(name, age, height, weight) {
  this.name = name,
  this.age = age,
  this.height = height,
  this.weight = weight
}

// 把sayHi()變成Person.prototype
Person.prototype.sayHi = function(){
    console.log(this.name + " says hi.")
}

let ming = new Person("小明", 28, 179, 70)
let hua = new Person("小華", 30, 169, 60)

ming.sayHi() // 小明 says hi.
hua.sayHi() // 小華 says hi.

console.log(ming.sayHi === hua.sayHi) //true
```

### prototype Inheritance
當一個物件要繼承其他物件prototype時，可以用`Object.create()`指定要繼承的prototype
這裡舉例人有不同的「工作者」。工作者的名字、年紀、身高、體重、打招呼都繼承自人。
- constructor function 用到 bind, call, apply 來繼承 object properties
- prototype 用`Object.create()`指定要繼承的prototype
```js
function Person(name, age, height, weight) {
  this.name = name,
  this.age = age,
  this.height = height,
  this.weight = weight
}

Person.prototype.sayHi = function(){
    console.log(this.name + " says hi.")
}

function Worker(name, age, height, weight, job){
  Person.call(this, name,age,height,weight)
  this.job = job
}

Worker.prototype = Object.create(Person.prototype)

let ming = new Worker("小明", 28, 179, 70,"工程師")
let hua = new Worker("小華", 30, 169, 60,"老師")

console.dir(ming) // Worker {name: "小明", age: 28, height: 179, weight: 70, job: "工程師"}
console.dir(hua) // Worker {name: "小華", age: 30, height: 169, weight: 60, job: "老師"}

```

[該來理解 JavaScript 的原型鍊了](https://blog.techbridge.cc/2017/04/22/javascript-prototype/)
