---
var:
  header-title: "オンラインテキストテンプレート"
  header-date: "2024/04/23"
---

# 教育カリキュラム

## 概要

### 前回の復習

- ここに前回学んだもの(予定だとHTMLとCSS)の復習を書く。

### 今回の講義の達成目標

<div class="note type-intro">
**達成目標**

1. JavaScriptの基本的な記述方法を学ぼう。

2. 
</div>

## Anime.jsを使用したアニメーションの作成

- Anime.jsは、軽量で柔軟なJavaScriptアニメーションライブラリです。CSSプロパティ、SVG、DOM属性、そしてJavaScriptオブジェクトをアニメーション化することができます。このライブラリを使用すると、複雑なアニメーションを簡単に作成でき、Webページに動的な視覚効果を加えることが可能です。

### Anime.jsの基本

- Anime.jsを使用するには、まずライブラリをページに含める必要があります。以下のスクリプトタグをHTMLに追加して、Anime.jsを読み込みます。

```html{.numberLines caption="index.html"}
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
```

- 基本的なアニメーションの設定は非常にシンプルです。以下の例では、CSSセレクタを指定して、特定の要素をアニメーション化します。

```javascript{.numberLines caption="main.js"}
anime({
  targets: '.box',
  translateX: 250,
  rotate: '1turn',
  duration: 2000,
  loop: true
});
```

- このコードは、クラス名`box`の要素を右に250ピクセル移動させ、1回転させるアニメーションを作成します。アニメーションの期間は2000ミリ秒で、これが無限に繰り返されます。

<iframe height="300" style="width: 100%;" scrolling="no" title="anime1" src="https://codepen.io/YasaiRa-men/embed/dyBjJKV?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/dyBjJKV">
  anime1</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### Anime.jsの応用

- Anime.jsは、キーフレームを使用したアニメーションや、複数のアニメーションプロパティの同時制御もサポートしています。以下の例では、複数のアニメーションプロパティを同時に制御し、より複雑なアニメーションを作成しています。

```javascript{.numberLines caption="main.js"}
anime({
  targets: '.box',
  translateX: [
    { value: 250, duration: 1000 },
    { value: 0, duration: 1000 }
  ],
  rotate: {
    value: '1turn',
    easing: 'easeInOutSine'
  },
  scale: [
    { value: 2, duration: 1000, delay: 500 },
    { value: 1, duration: 1000 }
  ],
  delay: 1000, // アニメーション開始までの遅延
  loop: true
});
```

- このコードでは、`translateX`, `rotate`, `scale`の各プロパティを使用して、要素を移動、回転、拡大縮小するアニメーションを作成しています。各プロパティは個別に時間を制御でき、より精密なアニメーションが可能です。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/ExBpopN?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/ExBpopN">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 障害物の落下

- これまでの知識を活かすと、このように上から1秒ごとに鼠色の背景の範囲内でランダムなX座標から障害物(黒い丸)を落下させることができます。

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/YasaiRa-men/embed/PoraGZd?default-tab=html%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/YasaiRa-men/pen/PoraGZd">
  Untitled</a> by バナナフライ (<a href="https://codepen.io/YasaiRa-men">@YasaiRa-men</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## まとめ

- Anime.jsを使用することで、Webページにスムーズで魅力的なアニメーションを簡単に追加できます。このライブラリは、その柔軟性とパワフルな機能により、デベロッパーにとって非常に有用なツールです。