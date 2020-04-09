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


## 要素の追加
1. 要素を作る
1. 中身のテキストを作る
1. DOMツリーに追加する

```HTML:index.html

  <ul>
    <li>item 0</li>
    <li>item 1</li>
    //ここにli要素を追加したい
  </ul>
```
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const item2 = document.createElement('li');   //li要素を作成
    item2.textContent = 'item 2';                 //中身のテキストを作成

    // const ulNode = document.querySelector('ul');  //ul要素を取得
    const ul = document.querySelector('ul');         //左は定数名、右は文字列であることを区別
    ul.appendChild(item2);                           //item2をDOMツリーに追加
  });
}
```
`createElement()`で要素を作成
`appendChild()`でDOMツリーに追加


## 要素の複製と、挿入
1. 要素を複製して
1. DOMツリーに追加
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const item0 = document.querySelectorAll('li')[0]; //li[0]要素を取得して、複製する
    const copy = item0.cloneNode(true);               //trueで中身のテキストもコピー、falseは中身コピーしない

    const ul = document.querySelector('ul');         //ul要素の取得
    const item2 = document.querySelectorAll('li')[2]; //li[2]要素を取得
    ul.insertBefore(copy, item2);                     //copyをitem2の前に挿入する
  });
}
```
`cloneNode()`でコピーする
`insertBefore(挿入するもの, 挿入するものの直後)`


## 要素の削除
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const item1 = document.querySelectorAll('li')[1]; 

    item1.remove(); 
  });
}
```
これは、古いブラウザでは適用されないことがあるので
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const item1 = document.querySelectorAll('li')[1]; 

    // item1.remove(); 
    //親Node.removeChild(削除するNode); 
    document.querySelector('ul').removeChild(item1); 
  });
}
```
`親Node.removeChild(削除するNode);`で表す


## input要素を操作
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const li = document.createElement('li');             //li要素を作る
    const text = document.querySelector('input'); 　　　　//input要素を取得する
    li.textContent = text.value; 　　　　　　　　　　　　　　//liの中身をinputされたものにする 
    document.querySelector('ul').appendChild(li);        //ulにliを追加する
                                                        //入力されたものがli要素として出力される
    text.value = ''; 　　　　　　　　　　　　　　　　　　　　　//inputを空白にして、　
    text.focus(); 　　　　　　　　　　　　　　　　　　　　　　　//新たにfocusする
  });
}
```


## セレクトボックスの操作
```HTML:index.html
<body>
  <select>
    <option value="red">赤</option>
    <option value="bule">青</option>
    <option value="yellow">黄</option>
  </select>
  <button>Add</button>

  <ul>
  </ul>
  
  <script src="js/main.js"></script>
</body>
```
```js:main.js
{ 
  document.querySelector('button').addEventListener('click', () => {
    const li = document.createElement('li');                  　　　　//li要素を作成する
    const color = document.querySelector('select'); 　　　　　　　　　　//select要素を取得する
    li.textContent = `${color.value} - ${color.selectedIndex}`;　　　//value属性とindexの表示
    document.querySelector('ul').appendChild(li); 　　　　　　　　　　　//li要素をDOMツリーに追加
  });
}
```

## ラジオボタンを操作
```HTML:index.html
<body>
  <input type="radio" name="color" value="red">赤
  <input type="radio" name="color" value="blue">青
  <input type="radio" name="color" value="yellow">黄
  <button>Add</button>
  
  <ul>
  </ul>
  
  <script src="js/main.js"></script>
</body>
```
```js:main.js
'use strict';

{ 
  document.querySelector('button').addEventListener('click', () => {
    const colors = document.querySelectorAll('input');   //input要素を取得
    let selectedColor;                                    //値を保持するための変数を宣言

    colors.forEach(color => {                           //colorの要素それぞれに対して
      if (color. checked === true) {　　　　　　　　　　　　//チェックされているか確かめる
        selectedColor = color.value; 　　　　　　　　　　　//チェックされていたら、valueの値を変数に代入する
      }
    }); 

    const li = document.createElement('li'); 　　　　　　//li要素を作成する
    li.textContent = selectedColor;                    //selectedColorをliのテキストに代入する
    document.querySelector('ul').appendChild(li); 　　　//親Nodeulに子Nodeliを追加する
  });
}
```
