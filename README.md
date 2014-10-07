# Kifu for JS (ver. 1.0.2)
JavaScriptで動く棋譜再生盤とそのブックマークレット
## 概要
* Kifu for JSは，Kifu for FlashやJava同様，HTML内で棋譜を読み込み表示，再生を行う．
	* **KIF**, **KI2**, [**JKF**](https://github.com/na2hiro/json-kifu-format)形式に対応．**CSA**形式はもうすぐ対応
* Kifu for JSブックマークレットは，1クリックでKifu for FlashやKifu for JavaをKifu for JSに置き換えて盤面を表示する．	
* Flash, Javaなどを必要としないため，iOSやAndroidでも表示できる

## Kifu for JS ブックマークレット
### 使い方
ブックマークレット本体は`src/bookmarklet.min.js`にあり

1. 次のコードをブックマークへ追加する→
`javascript:!function(){var s=document.createElement("script");s.src="https://na2hiro.github.io/Kifu-for-JS/src/public-bookmarklet.min.js",document.body.appendChild(s)}();void 0;`
2. Kifu for FlashやKifu for Javaが使われているページを開く
![](https://na2hiro.github.io/Kifu-for-JS/readme-ss/1.png)
3. ブックマークレットを開く
![](https://na2hiro.github.io/Kifu-for-JS/readme-ss/2.png)
4. FlashやJava部分が置き換えられ，Kifu for JSの再生盤になる
![](https://na2hiro.github.io/Kifu-for-JS/readme-ss/3.png)

## Kifu for JS
### 使い方
`test/loadKif.html`に例

jQuery(2.1以降で動作確認), kifuforjs.js, kifuforjs.cssを読み込む．ImageDirectoryPathには駒画像ファイルのあるディレクトリを指定する．

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<link rel="stylesheet" type="text/css" href="../css/kifuforjs.css">
<script src="../src/kifuforjs.js" charset="utf-8"></script>
<script>Kifu.settings={ImageDirectoryPath: "../images"};</script>
```

Kifu.load関数にkifファイルのアドレスを渡して呼び出すと，この場所に盤面を表示する．

```html
<script>Kifu.load("../json-kifu-format/jt201409130101.kif");</script>
```

第二引数にidを渡すと，このコードがある場所ではなく，そのidを持つ要素の子の位置に盤面を挿入する．この方法の場合，ひと通り読み込みが済んでから挿入されるため，head内などにあってもよい．

```html
<script>Kifu.load("../json-kifu-format/jt201409130101.kif", "board");</script>
〜
<div id="board"></div>
```

## 動作環境
以下は確認済み．

* Mac Chrome 37
* Mac Firefox 32
* Mac Safari
* Windows Internet Explorer 11
* Android Chrome 37
* Android Firefox 32
* Android Habit 1.1
* iOS 8 Safari

以下は手元に確認環境がありません．情報を[@na2hiro](https://twitter.com)までお待ちしています．

* Internet Explorer 10以下

## TODO
* [issues](https://github.com/na2hiro/Kifu-for-JS/issues)参照．
	* 要望やバグ報告もこちらへよろしくお願いします．
* 棋譜形式そのものへの対応については[json-kifu-formatのissues](https://github.com/na2hiro/json-kifu-format)参照．

## license
[Shogi images by muchonovski](http://mucho.girly.jp/bona/) below `images` directory are under a [Creative Commons 表示-非営利 2.1 日本 License](http://creativecommons.org/licenses/by-nc/2.1/jp/).

Other files are released under MIT license. See LICENSE.txt.
