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


## 条件演算子
if else 文の省略式
```js:main.js
条件式 ? true時の処理 : false時の処理
```
例
```js:main.js
const score = 85; 

score >= 80 ? console.log('Great!') : console.log('OK...')
```
> Great!

コードが読みにくくなる場合があるので、注意が必要


## 論理演算子
```js:main.js
const score = 60; 
const name = 'sato'; 

if (score >= 50) {
  if (name === 'sato') {
  console.log('Good job!'); 
  }
}
```
このようにif文を重ねることができるが、

```js:main.js
if (score >= 50 && name === 'sato') {
  console.log('Good job!'); 
}
```
論理演算子を用いる方が整っている

* && なおかつ(and)
* || もしくは(or)
* !  ~ではない(not)


## switch文で条件分岐
```js:main.js
const signal = 'green'; 

if (signal === 'red') {
  console.log('stop'); 
}
else if (signal === 'yellow') {
  console.log('Caution'); 
}
else if (signal === 'blue') {
  console.log('Go'); 
}
```
このようにif文で条件式が`(a === b)`のような場合は __switch文__ で書くことができる

```js:main.js
const signal = 'green'; 

switch (signal) {
  case 'red': 
    console.log('Stop'); 
    break; 
  case 'yellow': 
    console.log('Caution'); 
    break; 
  case 'blue': 
  case 'green': 
    console.log('Go'); 
    break; 
  default: 
    console.log('Wrong signal'); 
    break; 
}
```


## for文のループ処理
```js:main.js
for (let i=1; i <= 10; i++) {
  console.log('hello'); 
  console.log('hello' + i); 
}
```

`console.log('hello' + i)`は __テンプレートリテラル__ を用いて`console.log(`hello ${i}`)`と表すこともできる。

`${a}`で文字列として扱う

```js:main.js
for (let i=1; i <= 10; i++) {
 console.log(`hello ${i}`);
}
```


## while文
```js:main.js
let hp = 100; 

while (hp > 0) {
  console.log(`${hp} HP left!`); 
  hp -= 15; 
}
```

変数が条件を満たす間、繰り返される。

## do while文
```js:main.js
let hp = -50; 

do {
  console.log(`${hp} HP left!`); 
  hp -= 15; 
} while (hp > 0);
```

条件式を満たさなくても、最初の一度は実行される。

## ccontinue, break文
```js:main.js 
for (let i = 1; i <= 10; i++) {
  if (i === 4) {
  continue; 
  }
  console.log(i)
}
```
`continue`で指定された処理を飛ばす。

ちなみに
```js:main.js
if (i % 3 === 0) {
    continue; 
  }
```
これで3の倍数時飛ばす。

```js:main.js
for (let i = 1; i <= 10; i++) {
 if (i === 4) {
    break; 
  }
  console.log(i)
}
```
`break`は指定された処理までで強制的に終了させる。


## 関数で処理をまとめる
```js:main.js
function showAd() {
  console.log('--------------'); 
  console.log('------ Ad ----'); 
  console.log('--------------'); 
}

showAd(); 
console.log('Tom is great!'); 
console.log('Bob is great!'); 
showAd(); 
console.log('Steave is great!'); 
console.log('Richard is great!'); 
showAd(); 
```
`function showAd()`で処理をまとめる。そして、`showAd()`で関数を呼び出す。


## 引数
関数に値を渡してそれを使いたい時
```js:main.js
function showAd(message) {　　//仮引数
  console.log('--------------'); 
  console.log(`--- ${message}---`); 
  console.log('--------------'); 
}

showAd('Header Ad'); //実引数
console.log('Tom is great!'); 
console.log('Bob is great!'); 
showAd('Ad'); 
console.log('Steave is great!'); 
console.log('Richard is great!'); 
showAd('Footer Ad'); 
```
関数を呼び出す時に()で渡される値を __実引数__ 、定義内で仮に置かれる引数を __仮引数__ 

```js:main.js
function showAd(message = 'Ad')
showAd(); 
```
引数が渡されなかった時のデフォルトの値を決めることもできる。


## returnによる返り値
```js:main.js
function sum (a, b, c) {
  return a + b + c;
}

const total = sum (1, 2, 3) + sum (4, 5, 6);

console.log(total); 
```

`return`とすることで値を呼び出し元に返すことができる


## 関数式

### 関数宣言
```js:main.js
function 関数名(仮引数, 仮引数,,,) {
  処理; 
  処理; 
  return 返り値;
}

関数名(実引数, 実引数,,,);
```

### 関数式
```js:main,js
const  定数名 = function(仮引数, 仮引数,,,) {
  処理; 
  処理;
  return 返り値; 
}; 

定数名(実引数, 実引数,,,); 
```
`function(){};`ブロックの最後を __;__ (セミコロン)で閉じる。
またfunction関数は『無名関数』と呼ばれる。

例
```js:main.js
// function sum(a, b, c) {
//   return a + b + c;
// }

const sum = function(a, b, c) {  //関数式
  return a + b + c;
};

const total = sum(1, 2, 3) + sum(4, 5, 6); 
console.log(total); 
```
>21


## アロー関数
関数式を省略した形でかける

```js:main.js
// const sum = function(a, b, c) {
//   return a + b + c;
// };

const sum = (a, b, c) => a + b + c;

const total = sum(1, 2, 3) + sum(4, 5, 6); 
console.log(total); 

// const double = function(a) {
//   return a * 2; 
// }; 

const double = a => a * 2; 

console.log(double(12)); 
```
>21

>24

ブロックの中がreturnを返すだけであればreturnの値だけ書けば良い。また引数がひとつの場合は()も省略できる


## スコープ
スコープとは有効範囲のこと
```js:main.js
const x = 2; 

function f() {
  const x = 1; 
  console.log(x)
}

f(); 
console.log(x); 
```
ブロック外で宣言した場合は、この定数は全ての範囲で有効で、このようなスコープを __グローバルスコープ__ という。
ただし、ブロック内で同名の定数が定義されていた場合は、その中ではそちらが優先される。

### コードをブロックで囲ってスコープを分ける
```HTML:index.html
  <script src="js/main.js"></script>
  <script>
    'use strict'; 

    {
      const x = 300; 
      console.log(x); 
    }
  </script>
</body>
</html>
```

```js:
main.js
'use strict'; 


{
  const x = 100; 
  console.log(x); 
}
```

scriptタグを分けて書いてもスコープが分かれるわけではない。ブロックで分けることで、同名の定数を違う値として扱うことができる
__書いたコードはブロックで分ける
