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
