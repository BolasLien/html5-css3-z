## callstack

stack 堆疊

JavaScript是single thread的關係，所以呼叫function的時候會一層層堆疊，然後從最後進來的function開始釋放記憶體。(先進後出 FILO, First-in-Last-out)

### 實際執行function會發生的事情
1. call function
2. function do somethings
3. function finish and than return