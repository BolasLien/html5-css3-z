
## Class 類
- ES6才新增的寫法，但`class`的寫法只是語法糖
- 用來取代 prototype-based inheritance 的寫法，意思是用constructor function可以做物件的模板，改用class的語法也是做一樣的事情。好處是程式碼看起來比較整潔。
- 並沒有物件導向的繼承概念

```js
class Fruit {
  constructor(name, price) {
    this.name = name,
      this.price = price
  }

  getPrice() {
    console.log(`${this.name}的價格是${this.price}元。`)
  }
}

let apple = new Fruit("蘋果", 25)
apple.getPrice()
```

### extends and super
- 定義一個類別要繼承某個類別，用extends keyword
- 如果constructor或methods要繼承父類別，用super keyword

```js
class TaiwanFruit extends Fruit {
  constructor(name, price, location) {
    // constructor裡面 super代表父類別的constructor
    super(name, price)
    this.location = location
  }

  getPrice(){
    // 在methods裡面，super代表父類別
    console.log(super)
    super.getPrice()
    this.getLocation()
  }

  getLocation() {
    console.log(`${this.name}的產地是${this.location}。`)
  }
}

let mango = new TaiwanFruit("愛文芒果", 50, "獅子鄉")
mango.getPrice()
```

### static properties and methods 靜態屬性及方法
- 不需要實例化就可以直接使用類別的方法，也就是說不需要new一個物件
- 靜態方法常被使用在建立應用程式的工具函式(utility functions)

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
