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
|文字列



















