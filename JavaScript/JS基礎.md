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
