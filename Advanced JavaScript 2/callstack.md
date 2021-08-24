## callstack

stack 堆疊

JavaScript是single thread的關係，所以呼叫function的時候會一層層堆疊，然後從最後進來的function開始釋放記憶體。(先進後出 FILO, First-in-Last-out)

### 實際執行function會發生的事情
1. call function
2. function do somethings
3. function finish and than return

### 實用工具
* `console.trace()` 可以從開發模式看到呼叫時經過了那些地方。
* [這個網站可以輸入JS程式碼，以視覺化的方式看call stack的運作模式。](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gZjEoKSB7CiAgY29uc29sZS5sb2coJ1RoaXMgaXMgZjEnKQoKICBmMigpCgogIGZ1bmN0aW9uIGYyKCkgewogICAgY29uc29sZS5sb2coJ1RoaXMgaXMgZjInKQoKICAgIGYzKCkKCiAgICBmdW5jdGlvbiBmMygpIHsKICAgICAgY29uc29sZS5sb2coJ1RoaXMgaXMgZjMnKQoKICAgICAgY29uc29sZS5sb2coJ2YzIGRvbmUnKQogICAgfQoKICAgIGNvbnNvbGUubG9nKCdmMiBkb25lJykKICB9CgogIGNvbnNvbGUubG9nKCdmMSBkb25lJykKfQoKZjEoKQ%3D%3D!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)