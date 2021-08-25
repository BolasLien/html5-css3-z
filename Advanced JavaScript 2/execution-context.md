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