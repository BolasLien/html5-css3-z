
## Global Execution Context 全域執行環境

執行JS程式之前會做甚麼事情？

1. Creation Phase 創建階段
- window object被創造出來
- scope chain 被創造出來
- `this`被創造出來 (指向window object)
- Hoisting

2. Execution Phase 執行階段
一行一行的跑程式碼。跑程式碼的原則是 callstack.

## Function Execution Context 函式執行環境

function在執行之前會做甚麼事情？

1. Creation Phase 創建階段
- scope chain 被創造出來
- `this`被創造出來(如果 function 不是 arrow function的話)
- Hoisting

2. Execution Phase 執行階段
一行一行的跑程式碼。跑程式碼的原則是 callstack.

## Hoisting
### 結論
- 在 var 變數還沒被 assignment 的時候就被使用了，會得到undefined
- 在執行function declaration之前就呼叫function了，會正常執行function
- let 和 const 以及 function expression 不會有上述 hoisting 的結果

### 原因
Hoisting 發生在 execution context 的 creation phase 創建階段。

memories get allocated to all the functions declaration variable and var variables, not for the let and const and function expression. 記憶體會分配給 function的宣告 還有 var變數的宣告，但不會分配給 let 和 const (lexical declaration) 以及 function expression

Hoisting 指的是由於 functions declaration variable 及 var variables 在 creation phase 時被分配到記憶體當中，所以在 Execution Phase 時就可以在宣告之前使用。

```js 補充functions declaration 及 function expression
// function declaration 函式宣告
function sayHi1(){
  console.log("hi")
};
// function expression 函式表達式
const sayHi2 = function(){
  console.log("hi")
}
```


### 複習let, const, var
initializer 初始化變數的值
- const 必須初始化
- var, let 不用

re-declaration 重複宣告
- var 可以
- let, const 不可以

re-assignment 重新賦值
- var, let 可以
- const 不可以

