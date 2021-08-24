
## Class 類
- 用來取代 `prototype-based inheritance` 的寫法，意思是用 `constructor function` 可以做物件的模板，改用 `class` 的語法也是做一樣的事情。
- ES6 才新增的寫法，但`class`只是語法糖，所以 JavaScript 並沒有實作物件導向的繼承。
- 用 class 語法的好處是程式碼看起來比較整潔易懂。

```js
class Person {
  constructor(name, age, height, weight) {
    this.name = name,
      this.age = age,
      this.height = height,
      this.weight = weight
  }

  sayHi() {
    console.log(this.name + " 說 您好!");
  }
}

let ming = new Person("小明", 28, 179, 70)
ming.sayHi()
```

### extends and super 繼承及父類別
extends keyword
- 是用來定義一個類別要繼承某個類別

super keyword
- 在 constructor 裡必須先有 `super`，之後才能用 `this`。
- 需要在子類呼叫父類的 methods 時，用可以用 `super.method()`

```js
class Student extends Person{
  constructor(name, age, height, weight, education) {
    // constructor 裡面 super 代表父類別的 constructor
    super(name, age, height, weight)
    this.education = education
  }

  studentSayHi(){
    // 使用父類的 methods
    super.sayHi()
    console.log("我叫做" + this.name + "，我正在唸" + this.education)
  }
}

let hua = new Student("小華", 20, 169, 60, "大學")
hua.studentSayHi()
```


### static properties and methods 靜態屬性及方法
- 不需要實例化就可以直接使用類別的方法，也就是說不需要new一個物件
- 靜態方法常被使用在建立應用程式的工具函式(utility functions)

假設有 `Math` 這個工具函式，裡面有定義的屬性及方法為 `pi` 以及 `add()`，我們可以直接使用`Math.pi` 或 `Math.add()`。
```js
class Math{
  static pi = 3.14159
  static add(a,b){
    return a+b
  }
}

console.log(Math.pi); // 3.14159
console.log(Math.add(1,2)); // 3
```
