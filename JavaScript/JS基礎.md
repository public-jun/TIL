# JavaScript基礎文法

``` 
<body>
  
  <script src="js/main.js"></script>
</body>
```
HTMLファイルの中の<body></body>にいれる

```js:main.js
'use strict'; 
console.log('Hello World from main js!'); 
```

## 文字列の表示の仕方

```js:main.js
console.log('hello'); 
console.log("hello");
```
文字列は''(シングルクォーテーション)もしくは""(ダブルクォーテーション)で囲む

```js:main.js
console.log("it's me!"); 
console.log('it\'s me!'); 
```
文字列の中で'を使う場合は”で囲むか、直前に\(バックスラッシュ)をいれる

```js:main.js
console.log('hell\no wo\trld'); 
```
\nで改行、\tでタブ

```js:main.js
console.log('hello' + 'world'); 
```
+記号で文字列を連結する


## 四則演算

```js:main.js
console.log(10 + 3); 
console.log(10 - 3); 
console.log(10 * 3); 
console.log(10 / 3); 
console.log(10 % 3); //あまり
console.log(10 ** 3); //累乗

console.log(2 + 10 *3); 
console.log((2 + 10) *3); 
```

## 定数

```js:main.js
const price = 150; 

console.log(price * 140); 
console.log(price * 180); 
```
__const__ で定数を定義する


## 変数
constで与えられた値は再代入できないので、
```js:main.js
let price = 150; 

console.log(price * 140); 
console.log(price * 180); 

price = 200; 

console.log(price * 140); 
console.log(price * 180); 
```
変数letやvarで定義する

### 変数定数の命名規則
* 英数字、$、_のみで数字からはじめられない
* 大文字、小文字は区別される
* 予約後は使えない


## 変数を使った計算
```js:main.js
let price = 500;

// price = price + 100;
price += 100; 


// price = price * 2; 
price *= 2; 

// price = price + 1; 
// price += 1; 
price ++; 

// price -= 1; 
price --; 

console.log(price); 
```

## データ型について

|データ型|例|
|--:|:--|
|文字列(string)|'hello' '世界'|
|数値(number)|5 4.3 -20|
|Undefined|undefined|
|Null|null|
|真偽値(Boolean)|true false|
|オブジェクト(Object)|{a:3, b:5}|

`typeof`演算子を使うことで型がわかる

```javascript:main.js
console.log(typeof 'hello'); 
console.log(typeof 5); 
console.log(typeof true); 
console.log(typeof undefined); 
console.log(typeof null); 
```
>string

>number

>boolean

>undefined

>object


## 数字の文字列を使う
```js:main.js
console.log('5' * 3); 
console.log('5' - 3); 
```
>15

>2

数字からなる文字列も数値に変換して計算される

ただし
```js:main.js
console.log('5' + 3); 
```
>53

文字列と数値の間に+演算子を使うと、文字列の連結として扱われる

なので
```js:main.js
console.log(parseInt('5', 10) + 3); 
```
>8

`parseInt('5', 10)`これは文字列の5を整数値の10進数の5として扱う.

```js:main.js
console.log(parseInt('hello', 10)); 
```
>NaN

`parseInt('hello', 10)`で数値にしようとしたができないので`Not a Number`とでる


## 比較演算子

```js:main.js
const price = 1200; 

console.log(price > 1000);  //true
console.log(price < 1000);  //false
console.log(price >= 1000); //true
console.log(price <= 1000); //false
console.log(price === 1000);//false
console.log(price !== 1000);//true
```

false <- 0, null, undefined, '', false
true  <- それ以外

```js:main.js
console.log(Boolean(0)); 
console.log(Boolean('hello')); 
```
>false

>true

`Boolean()`で中身を評価することがでる

## if文で条件分岐

```js:main.js
if(条件式) {
  true時の処理
} 
else if (条件式) {
 if　がfalse　でelse if がtrueの処理
} 
else {
 それ以外の式
 }
```

例
```js:main.js
const score = 40; 

if (score >= 80) {
  console.log('Great!'); 
} else if (score >= 60) {
  console.log('Good!'); 
} else {
  console.log('OK...'); 
}
```
>OK...





