## Logical Operator 邏輯運算

- 邏輯運算代表一定會回傳一個 Boolean value 的結果

### 邏輯運算符號

- `>` 左邊 大於 右邊
- `<` 左邊 小於 右邊
- `>=` 左邊 大於等於 右邊
- `<=` 左邊 小於等於 右邊
- `==` is comparing if the values are the same on both sides type is different, but value is the same 兩邊的**值**是否一樣
- `===` is comparing if the values and type are the same both sides 兩邊的**值**與**資料型別**是否一樣
- `!=` values are different 兩邊的**值**是否不一樣
- `!==` values and types are different 兩邊的**值**與**資料型別**是否不一樣

### and, or operator 且，或 運算
假設 `A` 跟 `B` 為 Boolean value
- `A && B` → 當 `A` 是 `true` 且 `B` 是 `true`，結果為 `true`（兩者true，結果true）
- `A || B` → 當 `A` 是 `true` 或 `B` 是 `true`，結果為 `true`（其一true，結果true）

### if statement and condition syntax

下列語法表示：如果 `條件成立` 就做甚麼事情 `否則` 就做甚麼事情
```js
if (condition) {
  // doSomething....
} else {
  // doSomething....
}
```

- `condition` 都會變成 `truthy and falsy value` 來判斷
- 如果要判斷是不是 `NaN` ，就要用 `isNaN()`，因為不管用甚麼值去跟 `NaN` 比較，都會回傳 `false`

### Truthy and Falsy Values

**Falsy Value** 是指下列這六個值：

1. `false`
2. `0`
3. `""`  空字串
4. `null`
5. `undefined`
6. `NaN`

這六個以外都是 **Truthy value**

