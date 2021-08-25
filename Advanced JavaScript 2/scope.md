## Scope in JS
scope (n.) 範圍

- 它會決定變數的accessibility(visibility)，也就是說Scope是決定你的程式碼在哪個範圍是有意義的。
- JS有三種scope
1. Global Scope
2. Function Scope
3. Block Scope

### Global Scope (var, let, const)
在JS裡面，宣告在最外層的地方都是有意義的(可以訪問的)。
```js
let myName = 'Bolas'

function sayHi() {
  console.log(myName + " says good morning.")
}
```
### Function Scope (var, let, const)
if a variable has function scope, then it can only be seen inside the function.
it has no meaning outside the function.

如果變數有function scope，它在function內才能被看到(可以訪問)。
它如果在function外就沒有意義。

### Block Scope (let, const)
a variable that has block scope means
it can only be seen inside a loop or a if statement

變數有block scope表示
它在loop或if語法裡面才能被看到(可以訪問)。

### var variable in for loop
用 loop 時如果用同名的var變數，就會被loop改變值。

這是因為 var 沒有 block scope，所以不管在任何地方都能被看到(可以訪問)。

也就是為什麼開發上盡量不使用var變數。

```js
var x = 1

for(var x = 0; x < 10; x++) {
  console.log(x)
}

console.log(x) // 10
```

### 小抄
![](./variables.png)