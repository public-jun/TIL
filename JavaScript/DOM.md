# DOM

## DOMの概要

### ブラウザの仕組み
HTMLファイルを読み込むと、Document Object File(DOM)と呼ばれるデータ構造が作られ、その内容に応じてページが描画される
このDOMをJavaScriptで操作して、様々な機能をえる
* JavaScriptで内容を書き換えても、HTMLが変更されるわけではない。

## 要素を操作する
```HTML:index.html
<body>
  <h1 id="target">ドットインストール</h1>
  <p>こんにちは。こんにちは。こんにちは。</p>
  <p>こんにちは。こんにちは。こんにちは。</p>
  <p>こんにちは。こんにちは。こんにちは。</p>

  <script src="js/main.js"></script>
</body>
```

```js:main.js
document.querySelector('h1').textContent = 'Changed!'; 
```
または
```js:main.js
document.querySelector('#target').textContent = 'Changed!'; 
```
これで操作できる。

DOMは`document`という特殊なオブジェクトで扱うことができて、文章内から特定の要素を取得するには`querySelector()`というメソッドを使う

### `id`を指定することもできる
```js:main.js
document.getElementById('target').textContent = 'Changed!'; 
```
idで指定する場合は、`getElementById()`というメソッドを使う。これはセレクターではなく、idの名前をそのまま書けばいいので、#がいらない。


## 複数の要素を取得する
```js:main.js
 document.querySelector('p').textContent = 'Change!'; 
```
 `querySelecotr`はこのセレクターで見つかった要素のうち最初のものしか取得できない。
 
 documentにある全ての要素を取得したい場合は、、、
 ```js:main.hs
 document.querySelectorAll('p')[1].textContent = 'Change!'; 
 ```
 `querySelectorAll`で全ての要素を取得することができる。
 
 ### 全ての要素を処理したい場合
 `forEach()`を用いる
 ```js:main.js
 document.querySelectorAll('p').forEach((p, index) => {
      p.textContent = `${index}番目のpです!`;
    });
 ```
 
 * __id属性がついていたら、`getElementById()`__
 * __id属性がついていなかったら、`querySelector()`もしくは、`querySelectorAll()`__
 
 
 ## 要素の取得
 
 ### 要素を取得する方法
 * idやセレクターを指定して要素を取得する
 * DOMツリーの階層関係から要素を取得する


## addEventListener() 
よりインタラクティブにする
```js:main.js
addEventLisetner('イベントの種類の文字列', 実行したい処理の関数)
```

例
```HTML:index.html
<button>Run</button>
```
```js:main.js
{
  document.querySelector('button').addEventListener('click', () => {
    document.getElementById('target').textContent = 'Change!'; 
  }); 
}
```
 

## 要素の属性を操作
```js:main.js
{
  document.querySelector('button').addEventListener('click', () => {
    const targetNode = document.getElementById('target');

    targetNode.textContent = 'Change!';       
    targetNode.title = 'This is title!';     //document.getElementById('target').title
    targetNode.style.color = 'red'; 
    targetNode.style.backgroundColor = 'skyblue'; //cssで-(ハイフン)を使うようなものは大文字にする
  }); 
}
```
JavaScriptでは`backgroundColor`と表す。


## className 
classはJSでは予約語になるので、クラス属性を扱う場合は`className`を使う
```HTML:index.html
<head>
  <meta charset="utf-8">
  <title>JavaScript Basics</title>
  <style>
    .my-color{
      color: red; 
      background-color: skyblue;
    }

    .my-border {
      border-bottom: 4px solid orange; 
    }

  </style>
</head>
<body>
  <button>Run</button>

  <h1 id="target" class="my-border">プログラミング学習</h1>
  <p>こんにちは。こんにちは。こんにちは。</p>
  <p>こんにちは。こんにちは。こんにちは。</p>
  <p>こんにちは。こんにちは。こんにちは。</p>

  <script src="js/main.js"></script>
</body>
```
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const targetNode = document.getElementById('target');

    // targetNode.className = 'my-color';
    targetNode.className = 'my-color my-border';
  });
}
```
`className`はこの要素に他のクラスがすでについていれば注意が必要(上記では`my-border`がついている)
元からついているものもまとめて、書く必要がある。
`className`は元からついていたクラスも考慮しなければならない。


## classList
class属性の操作は __classList__ を使うと便利

### クラスの追加
```js:main.js
const targetNode = document.getElementById('target');

    // targetNode.className = 'my-color my-border';
    targetNode.classList.add('my-color');
```
`classList.add`で既存のクラス設定に`my-color`を追加してくれる。

### 要素に特定のクラスがついているか調べる
```js:main.js
targetNode.classList.contains('my-color')
```
これで特定のクラスがついているか、trueかfalseで返してくれる

### クラスの追加と外す
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const targetNode = document.getElementById('target');
    
    if (targetNode.classList.contains('my-color') === true ) {   //trueかfalseでしらべる
      targetNode.classList.remove('my-color'); 
    } else {
      targetNode.classList.add('my-color'); 
    }
  });
}
```
クリックするごとにクラスをつけたり外したりする

また、以下でも同じ意味になる
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const targetNode = document.getElementById('target');

    // if (targetNode.classList.contains('my-color') === true ) {
    //   targetNode.classList.remove('my-color'); 
    // } else {
    //   targetNode.classList.add('my-color'); 
    // }
    targetNode.classList.toggle('my-color');   //上と同じ
  });
```


## カスタムデータ属性
HTMLでは`data-`から始まっていれば独自の属性をつけることができる
```HTML:index.html
<h1 id="target" data-transration="Dotinstall">ドットインストール</h1>
```
JavaScriptからカスタムデータ属性の値にアクセスする場合は,,,
```js:main.js
targetNode.textContent = targetNode.dataset.transration;　　//dataset.transration
```
`detaset`と書いてアクセスする
