# JavaScript Basics

## variable 變數

等號(=)在程式語言是 assignment 的意思，把等號左邊的值放入右邊的變數。

假設變數是一個箱子，let / const / var 是三種箱子

constant (n.) 常數 (adj.)不變的

### re-assignment

let 可以
const 不可以
var 可以

### re-declaration

let 不可以
const 不可以
var 可以

## Numbers Operators 運算符號

加+ 減- 乘\* 除/

% remainder 餘數計算

^或\*\* power 次方計算

++ 加 1 x=x+1
-- 減 1 x=x-1

+=, -=, \*=, /= 算數的語法糖
x = x+10 => x += 10

## Strings 字串

"" 雙引號內的字都是字串

String Concatenate 串字串

"string" + "string" 這裡的加號是 concat (concatenation)
15 + 23 這裡的加號是 addition

不能減乘除
console.log("Goodbye" - "e") //結果為 NaN = Not a Number
JavaScript 不知道這個結果是什麼數字

如果是 "string" + number 這裡的加號是 concat

1. number to string
2. concat

如果是 number + number + string

1. number + number
2. number to string
3. concat

只要遇到字串加數字的情況，都會把數字算完，之後轉型為字串，再用 concat 串在一起

// 單行註解
/\* _/ 多行註解
/\*\* _/ vscode 快速註解

## Primitive Data Types 原始資料類型

- 在 JS 中最基本的六種資料類型
- JS 儲存資料的方式

1. Number
2. String
3. Boolean
4. Undefined
5. Null
6. Symbol

不在這六個裏面的都不是 Primitive Data Type(例如 Object)

#typeof Operator 判斷型別運算

#Logical Operator 邏輯運算

一定會回傳一個 Boolean 值

== ===
!= !==

> < >= <=

== is comparing if the values are the same on both sides
type is different, but value is the same

=== is comparing if the values and type are the same both sides

!= values are different
!== vlues and types are different

#and, or operator 且，或 運算
A,B 為 Boolean value
A && B => A 是 true 且 B 是 true
A || B => A 是 true 或 B 是 true

#if statement and condition syntax

如果 條件成立 就做甚麼事情，否則 就做甚麼事情
if (condition) {

} else {

}

condition 都會變成 truthy and falsy value 來判斷
如果要判斷是不是 NaN，就要用 isNaN()，因為不管用甚麼值去跟 NaN 比較，都會回傳 false

# Truthy and Falsy Values

Falsy Value

1. false
2. 0
3. "" => 空字串
4. null
5. undefined
6. NaN

這六個以外都是 truthy

# Variable Naming Convention 變數命名習慣

非強制性，但是大家都這樣做
camelCase 駝峰式命名 第一個單字小寫，之後的單字都大寫開頭
underline 底線 第一個單字跟之後的單字中間都用底線來區分
const with uppercase 常數全大寫 因為是不會改變的值，建議用全大寫，別人不須知道宣告的時候適用 const，也可以一看就知道是 const

# Variable Naming Restriction 變數命名限制

強制性，不這樣做就會錯
variable name cannot start with a number! 變數不可以用數字開頭
hyphen in JS is number operator 不能用減號(hyphone)

# Array 陣列

雖然是一種資料型態，但它不是一個原始資料型態

當你需要把資料一起儲存時，它會很實用
let friend1 = "Jonn"
let friend2 = "Amy"
let friend3 = "Ella"
let friend4 = "Grace"

=> let friends = ["John","Amy","Ella","Grace"]

Property 本身就帶有的屬性
index 索引
length 長度

methods 實用的函式
push(value) 加入陣列的最後一個
pop() 減去陣列的最後一個
shift() 減去陣列的第一個
unshift(value) 加入陣列的第一個

# Function 函數(函式)
跟程序很像，含有一系列的程式碼，用來執行任務(performs a task)或計算值(calculates a value)

JS 本身有 build-in function，但你也能自創 function

build-in function 內建的函數
console.log(),alert(),array.push()...

怎麼做自己的 function

1. function declaration
2. invoke, execute a function

function knowledge
parameter 參數
function fn1(parameter)
function fn2()

return key word 丟出
要用一個 Variable 接住，不然他只會執行而已

#  Object 物件
object declaration
let Bolas = {
// properties setting
firstName: "Bolas",
lastName: "Lien",
age:30,
is_married: true,
spouse: "Iris Wang",
// methods setting
sayHi(){
console.log("Hi, I am Bolas.")
},
walk(){
console.log("Bolas is walking on the street.")
}
}

object 取值
// [], dot notation
console.log(Bolas["age"]) //30
console.log(Bolas.age) //30
Bolas.sayHi() // Hi, I am Bolas.

typeof array 的結果是 object
Array is a special type of object
原因是 array 其實是一種特別的 object，並不是 array 是一種 data Type

#this key word
this 就是指這一個 object，下面的例子，this.age，的 this 指的就是 Bolas 這個物件。
let Bolas = {
age: 30,
sayAge(){
console.log("Bolas's age is " + this.age + " years old")
}
}
除此之外，如果在最外層，this 指的是 window 物件

# loop 迴圈

快速且簡單的方式來重複一樣的事情。
for loop
for(let i = 0;i <=10;i++){
console.log(i)
}
while loop
let j = 0;
while(j<=10){
console.log(j)
j++;
}

風險：因為沒有給結束條件的話，有可能會發生無窮迴圈(infinite loop)

keywords in loop
continue 跳脫迴圈，不執行目前接下來的事情了，繼續下一個動作
break 中斷迴圈，完全不做了

# 關於 loop 的其他議題
Nested loop
loop 裡面還有 loop
how to loop through an array
用 loop 取得陣列的每個值

# Math Object
Math = {
PI: 3.14159...,
pow(a,b){},//回傳 a 的 b 次方
random(){},//隨機給你 0~1 之間的數字(可能會回傳 0 但不會回傳 1)
sqrt(){},//回傳開根號的結果
abs(){},//回船轉正數
floor(){},//回傳無條件捨去小數點
ceil(){},//回傳無條件進位小數點
}

# Reserved words in JS 保留字
命名限制 (Restriction)
強制性，不能被當作變數名稱的字。
let, const, return, break, continue...
