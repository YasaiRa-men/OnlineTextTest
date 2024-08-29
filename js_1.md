---
var:
  header-title: "オンラインテキストテンプレート"
  header-date: "2024/04/23"
---

# 教育カリキュラム

## 概要

### 前回の復習

- JavaScriptの書き方について学んだ

### 今回の講義の達成目標

<div class="note type-intro">
**達成目標**

・ゲームに使用している関数などについて学ぼう
</div>

## Documentオブジェクト

### Documentオブジェクトとは

- Documentオブジェクトは、Webページ全体を表すオブジェクトであり、HTML文書全体を操作するためのインターフェースを提供します。JavaScriptを使用して、HTML要素の取得や変更、新しい要素の作成などを行う際にDocumentオブジェクトが活用されます。

- 今回作成するゲームにて、テキストやボタンの位置、色などの変更はこれらによって指定されています。

- Documentオブジェクトは通常、`document` 変数を介してアクセスされます。

### HTML要素の取得

- Documentオブジェクトを使用すると、HTML要素を取得することができます。以下は、要素を取得する例です。

```html{caption="index.html"}
<div id="myElement" class="myClass"></div>
<script src="main.js"></script>
```

```javascript{.numberLines caption="main.js"}
// IDを使用して要素を取得
let elementById = document.getElementById("myElement");

// クラス名を使用して要素を取得
let elementsByClass = document.getElementsByClassName("myClass");

// タグ名を使用して要素を取得
let elementsByTag = document.getElementsByTagName("div");
```

- 今回の例だと、全て同じ要素を取得しています。

- これらを取得することによって、そのHTML要素の文字や色あどがJavaScriptで変更できるようになります。

### HTML要素の変更

- ひとまず、HTMLをこのように書いてみよう。

```html{caption="index.html"}
<p id="myElement"></p>
<script src="main.js"></script>
```

- Documentオブジェクトを使用して、<em>textContent</em>で取得したHTML要素の内容を変更することができます。以下は、要素の内容を変更する例です。

```javascript{.numberLines caption="main.js"}
let element = document.getElementById("myElement");
element.textContent = "新しいテキスト";
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/NWVNdmK?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/NWVNdmK">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

また、<em>style</em>でcssのスタイルを変更することができます。以下は、要素の内容を変更する例です。
```javascript{.numberLines caption="main.js"}
let element = document.getElementById("myElement");
element.textContent = "新しいテキスト";
element.style.color = "red";
```

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/MWdyJRj?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/MWdyJRj">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 新しい要素の作成

- Documentオブジェクトを使用して、新しいHTML要素を作成し、ページに追加することができます。以下は、新しい要素を作成してページに追加する例です。

```javascript{.numberLines caption="main.js"}
let newElement = document.createElement("p");
newElement.textContent = "新しい段落";
document.body.appendChild(newElement);
```

### Documentオブジェクトの活用

- Documentオブジェクトを活用することで、動的なWebページの作成や操作が可能となります。JavaScriptを使用して、ユーザーとのインタラクションやページの動的な変更を実現する際にDocumentオブジェクトは重要な役割を果たします。

<div class="note type-quiz">
Q. 以下のHTMLのp要素に「こんにちは」という文字を入れ、の背景を青に、横幅を100%にしよう。
```html{caption="index.html"}
<p id="myElement"></p>
<script src="main.js"></script>
```
<div class="quizes">
<div class="options">
  <div class="option correct">答えを見る</div>
</div>
<div class="answercontent">
答えの一例です。
<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/yLWVXjQ?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/yLWVXjQ">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
</div>
</div>
</div>

## イベントハンドリング

- イベントハンドリングは、ユーザーからの入力やアクションに応じてプログラムが反応する方法ですJavaScriptを使用すると、Webページ上のイベントを捕捉し、特定の処理を実行することができます。

```javascript{.numberLines caption="main.js"}
document.addEventListener(イベント, function() {
  // イベントが行われたときに実行されるところ
  console.log("イベントが発生しました。");
});
```

- イベントハンドリングはこのようにして追加することができます。（イベントについては後ほど解説します）

- addEventListenerの前のdocumentについて、`document`だとWeb全体でイベントを監視していて、特定の要素内でイベントを監視したいときには、Documentオブジェクトを書いてあげることで実現できます。

- また、イベントで行われる関数には、引数を設定することができ、この引数を使って様々なことができます。

```javascript{.numberLines caption="main.js"}
document.addEventListener("wheel", function(event) {
  // イベントが行われたときに実行されるところ

  event.preventDefault();
  console.log("イベントが発生しました。");

}, { passive: false });
```

- 例えば、ホイールでスクロールさせようとしたときに発生するイベントですが、上から下へホイールを動かした際に、ページが上にスクロールしてしまいます。

- このようなデフォルトの動作を無効にするために、`preventDefault();`というものがあり、これを書くことで無効にできます。

- また、詳しい解説は省きますが、`preventDefault();`を使用した際には、`addEventListener`の第二引数にpassiveをfalseにすることを宣言しておく必要があります。これをしておかないと、`preventDefault();`がブラウザによって機能しない可能性があります。

### イベントリスナーの追加

- イベントリスナーは、例えば、ボタンをクリックしたとき、マウスを動かしたとき、文字を入力したとき...など、様々なイベントが発生したときに呼び出されます。

- これを個別で追加することによって、ユーザーが行ったことを検知することができます。

- 以下は、ボタンクリックイベトにリスナーを追加する例です。

```html{caption="index.html"}
<button id="myButton">Click me!</button>
<script src="main.js"></script>
```

```javascript{.numberLines caption="main.js"}
let button = document.getElementById("myButton");

button.addEventListener('click', function() {

  alert('Button was clicked!');

});
```

- この例では、IDが `myButton` のボタンにクリックイベントリスナーを追加しています。ボタンがクリックされると、アラートが表示されます。

<iframe height="300" style="width: 100%;" scrolling="no" title="btnclick" src="https://codepen.io/YasaiRa-men/embed/vYqapZW?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/vYqapZW">
  btnclick</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

- 他にも、キーを押したときの`keydown`、画面をタッチ操作で動かしたときの`touchmove`,
マウスを動かしたときの`mousemove`などもあります。

- 以下の例では、マウスまたは画面を指でスライドしたときに黒丸がその場所に移動するサンプルコードです。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/abgKZOr?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/abgKZOr">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

- この丸を主人公に当てはめることで、常にマウスについてくるようになります。

## 距離計算

- 障害物に当たるとゲームオーバーになるようにするには、障害物との距離を計算する必要があります。

- そこで、それぞれのX座標とY座標は分かっているので、三平方の定理を利用することで距離を求めることができます。

![img](figs/js/kyori.png)

<iframe height="300" style="width: 100%;" scrolling="no" title="kyori2" src="https://codepen.io/YasaiRa-men/embed/poXKbpq?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/poXKbpq">
  kyori2</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

- `getBoundingClientRect()`はターゲット要素をの位置をブラウザの表示領域の左上を(0, 0)として、そこからの相対位置で示されています。これによって自分、または障害物がどこにあるのかを調べることができます。

```javascript{.numberLines caption="script.js"}
// 自分の位置を取得
const circleRect = circle.getBoundingClientRect();
// 障害物の位置を取得
const obstacleRect = obstacle.getBoundingClientRect();
```

- 距離計算の関数について解説します。

- 距離は、このように計算あうることで求めることができます。

$$距離=\sqrt{縦^{2} + 横^{2}}$$

- この式をJavaScriptで書いてみよう！

```javascript{.numberLines caption="script.js"}
// 三平方の定理で距離を計算
const distance = Math.sqrt(Math.pow(circleX - obstacleX, 2) + Math.pow(circleY - obstacleY, 2));
```

- `Math.pow()`は、累乗を計算できるもので、第一引数には累乗させたい数、第二引数には指数を書きます。上記の例だとそれぞれ自分の位置から障害物までの位置の差を取って、2乗していることが分かります。

- `Math.sqrt()`は、平方根を表します。

- これらによって、`distance`に計算された距離を代入されていることが分かりますね！

- テキストについての処理はここで行われています。

```javascript{.numberLines caption="script.js"}
// 距離をテキストで表示
distanceText.textContent = 'Distance: ' + Math.round(distance) + 'px';

// 衝突判定 (2つの半径の和より距離が小さい場合)
const radiusSum = circleRect.width / 2 + obstacleRect.width / 2;
    
if (distance <= radiusSum) {
    collisionText.textContent = '当たり判定：障害物に当たっています！';
} else {
    collisionText.textContent = '当たり判定：障害物に当たっていません';
}
```

- Math.round()は小数点以下を四捨五入できるものとなってます。試しに`Math.round(distance)`のところを`distance`に変更
してみるとどんな変化があるのか試してみよう！

- 下の条件分岐では、計算された距離が自分と障害物の丸の半径の合計より小さい場合、つまり当たっている場合で表示するテキストを変えています。

## まとめ

- このセクションでは、JavaScriptを使って、避けゲーの基盤となる部分を作成しました。

---

次回はこれらを組み合わせて実際にゲーム作りにとりかかりましょう！