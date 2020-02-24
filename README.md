# stardard-layout_modern-coding
『HTML5/CSS3モダンコーディング フロントエンドエンジニアが教える3つの本格レイアウト スタンダード・グリッド・シングルページレイアウトの作り方』を参考にサイトを作ってみた

[sample](https://tombo-gokuraku.github.io/stardard-layout_modern-coding/)

## 収穫
### コーディング時のポイント
* 要素名にスタイルを指定しない
→HTMLを編集するとCSSも一緒に編集しなければいけなくなるから


代わりにクラスにスタイルを指定する


**Bad**
```
<div class="container">
  <h2>hoge</h2>
</div>
```
```
.container h2 {
  color: black;
}
```
**Good**
```
<div class="container">
  <h2 class="heading">hoge</h2>
</div>
```
```
.heading {
  color: black;
}
```

* CSSのセレクタにはIDではなくクラスを使用する
理由
  * 同一ページ内にIDは1つしか使えないからスタイルの使い回しができない
  * IDは詳細度が高いからスタイルの上書きが難しい


IDはJavaScriptからHTMLのノードを指定したい時に使う

* remは便利!
remはroot emの略


html要素のfont-sizeを1とした時の倍率を指定できる。


主要なブラウザのフォントサイズは16pxなので、htmlのfont-sizeを62.5%にしておくと、10px相当にできる。


さらにpx指定ではなく%指定にすることで、ユーザーがブラウザのデフォルトの文字サイズを変更していた場合にもある程度その設定を反映させられる
```
html {
  font-size: 62.5%;
}
```

* 手順
  1. header,footer,mainなどの大枠を作る
  1. ベースとなるCSSを定義する
    * 使用するフォントの種類
    * ベースとなるフォントサイズ
    * テキストの文字色
    * リンクの文字色



### marginの相殺
ブロックレベル要素の上下のマージンは相殺される


例
```
<div class="box"></div>
<div class="box"></div>
```
```
.box {
  margin: 20px;
}
```
上のように設定すると、上下のdiv.boxに挟まれた空間のマージンは40pxではなく**20px**になる。


値が異なる場合は、大きい方のマージンが採用される
```
<div class="box"></div>
<div class="box-large"></div>
```
```
.box {
  margin: 20px;
}
.box-large {
  margin: 30px;
}
```
上の場合はマージンは30pxになる
[マージンの相殺](https://developer.mozilla.org/ja/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)

### CSS Reset
reset.cssとはブラウザごとに異なるユーザーエージェント(UA)スタイルシートを上書きするためのスタイルシート


normalize.cssとはUAスタイルシートを活かしつつ、ブラウザ間の差異のみ吸収するスタイルシート

### line-heightのプロパティ
指定方法:normal,数値+単位(px,em,remなど),割合(%),数値のみ
オススメは数値のみ,font-sizeが10pxでline-heightが1.5なら、行の高さは15pxになる。 **子要素に引き継がれると基準はその子要素のfont-sizeになる。**
line-heightの値は子要素にも引き継がれるので、数値+単位などで指定すると、子要素のfont-sizeが変わった時に行の高さが合わなくなる。

## ダメなところ
### 書籍が古いためか、あまりflexboxが使われていない
* clearfix
float使わなければいいだけ。今はflexがあるから、もう覚えなくてもいいと思ってる
* inline-block
* line-heightで中央揃え
### 計算した値を決め打ち
幅が少しでも変わったら終わり
p69



## Reference
https://www.shoeisha.co.jp/book/detail/978479814157z
