## Function Methods
- functions are objects in JS
- Bind, Call, Apply

## functions are objects in JS
function在JS裡都是objects，用console.dir的方式可以展開object，所以把function丟進去查看，可以發現function他繼承了function物件，而function物件又繼承object

```js
function hello(){
  console.log("hello");
}

console.dir(hello);
```

## Bind, Call, Apply
function的this是指向`window object`，如果我們需要改變function的this，可以用function物件繼承的方法：bind, call, apply，來達到改變this的指向。
這三個方法的用途都是在重新綁定function的this，差別在於寫法不一樣。

```js
let pocket = {
  money: 325,
}

let wallet = {
  money: 2000,
}

let bank = {
  money: 300400,
}

function getMoney() {
  console.log(this.money)
}

function updateMoney(location, numberOfMoney) {
  let total = this.money + numberOfMoney
  console.log(`${location}原本有${this.money}元。存了${numberOfMoney}進去，現在有${total}元。`)
  this.money = total
}

// Function.prototype.bind()
// let newFunction = originFunction.bind(thisArg)
// newFunction(parameter1, parameter2, ...);
let checkWalletMoney = getMoney.bind(wallet)
checkWalletMoney()
let updateMoneyIntoWallet = updateMoney.bind(wallet)
updateMoneyIntoWallet('皮夾', 300)

// Function.prototype.call()
// originFunction.call(thisArg, parameter1, parameter2, ...)
getMoney.call(pocket)
updateMoney.call(pocket, "口袋", 500)

// Function.prototype.apply()
// originFunction.apply(thisArg, [parameter1, parameter2, ...])
// parameter is an array
getMoney.apply(bank)
updateMoney.apply(bank, ["銀行", 80000])

console.log(pocket, wallet, bank); // {money: 825} {money: 2300} {money: 380400}
```
