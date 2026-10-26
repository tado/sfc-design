---
title: "反復と乱数"
date: "2026-10-11T14:51:13+09:00"
lastmod: "2026-10-17T09:45:59+09:00"
url: "/sfc-design26/19834.html"
categories: ["sfc-design26"]
summary: "今回は、プログラムの基本的な構造のひとつである「反復 (くりかえし)」について学びます。"
image: "/wp-content/uploads/2026/10/03_slide46.png"
wp_id: 19834
shortlink: "https://wp.me/pU1U9-59U"
---

<figure class="wp-block-image size-full"><a href="/wp-content/uploads/2026/10/03_slide46.png"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide46.png" alt="" class="wp-image-19837" srcset="/wp-content/uploads/2026/10/03_slide46-300x253.png 300w, /wp-content/uploads/2026/10/03_slide46-768x648.png 768w, /wp-content/uploads/2026/10/03_slide46.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></a></figure>

今回は、プログラムの基本的な構造のひとつである「反復 (くりかえし)」について学びます。

まず始めに、値を記憶しておく「変数」について解説します。変数を使うことで、手で計算しなくても、図形の大きさなどを少しずつ変化させながら描くことができるようになります。

次に、for文を使った「繰り返し」を学びます。同じ命令を何度も書くかわりに、くりかえしの回数を指定して一気に実行します。入れ子状の図形を描くクイズにも挑戦してみましょう。

最後に、実行するたびに異なる値を出力する「乱数」を導入します。乱数と繰り返しを組み合わせることで、偶然性や意外性をとり入れた表現が可能になります。

## スライド資料

[スライド資料: 反復と乱数](https://drive.google.com/file/d/1nx4HaOdf8v9eXiyDS3Ua4484sXVboRby/view?usp=sharing)

## 本日の課題

テーマ: 「乱数 (random) と繰り返し (for) を使用した表現」

今回学んだ乱数 (random) と繰り返し (for) を使用して、自由な発想で表現してみましょう! 次回の授業の冒頭で簡単に作品をいくつか紹介します。

- 完成した作品には、タイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出
- 必ず TAGS: [sfc261016](https://openprocessing.org/browse?q=sfc261016&time=anytime&type=tags&offset=0#) を入れてください
- 提出期限 10/22/2026

[課題提出フォーム](https://docs.google.com/forms/d/e/1FAIpQLSfhS3oIn2oNGNT-FwfUjKQLMedSXPpvTeUc80qJsDx341hINg/viewform?usp=dialog)

## 今日の内容

- 反復 (Iteration)
- 変数
- 繰り返し (for文)
- 乱数
- 乱数と繰り返し
- 実習

## 反復 (Iteration)

コンピューターは「くりかえし」の天才です! 最近のマシンであれば、1秒間に20億回（2GHz）以上のクロックで、正確に計算をくりかえすことができます。反復は、プログラムの基本的で重要な構造のひとつです。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="800" src="/wp-content/uploads/2026/10/03_slide03.png" alt="CPU" class="wp-image-19847" srcset="/wp-content/uploads/2026/10/03_slide03-150x150.png 150w, /wp-content/uploads/2026/10/03_slide03-300x300.png 300w, /wp-content/uploads/2026/10/03_slide03-768x768.png 768w, /wp-content/uploads/2026/10/03_slide03.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

### 構造化プログラミング

構造化プログラミングでは、プログラムを以下の3つの構成要素の組み合わせで考えます。

- 順次実行 (Sequence)
- 分岐 (Selection)
- 反復 (Iteration)

![順次・分岐・反復](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide04.svg)

すべてのアルゴリズムは、この3つの基本的な制御構造を使用して表現できます。これを「構造化定理」と呼びます。

1. 順次実行（Sequence）: 命令は上から下へと順番に実行される
2. 選択（Selection）: 条件分岐、「もし○○なら××しなさい、そうでなければ△△しなさい」
3. 反復（Iteration）: 繰り返し → **本日の主題**

## 変数

### クイズ

まずはクイズです。正方形の中に、ちょうど半分の幅と高さの正方形を描いてみましょう。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="480" height="502" src="/wp-content/uploads/2026/10/03_slide07.png" alt="正方形の中に半分の正方形" class="wp-image-19843" srcset="/wp-content/uploads/2026/10/03_slide07-287x300.png 287w, /wp-content/uploads/2026/10/03_slide07.png 480w" sizes="auto, (max-width: 480px) 100vw, 480px" /></figure>

答えは以下のようになります。

```javascript
function setup() {
  createCanvas(400, 400);
  rect(100, 100, 200, 200);
  rect(100, 100, 100, 100);
}
```

クイズ2です。さらに半分の正方形を中に描いてみましょう。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="480" height="502" src="/wp-content/uploads/2026/10/03_slide09.png" alt="さらに半分の正方形" class="wp-image-19840" srcset="/wp-content/uploads/2026/10/03_slide09-287x300.png 287w, /wp-content/uploads/2026/10/03_slide09.png 480w" sizes="auto, (max-width: 480px) 100vw, 480px" /></figure>

答えは以下のようになります。

```javascript
function setup() {
  createCanvas(400, 400);
  rect(100, 100, 200, 200);
  rect(100, 100, 100, 100);
  rect(100, 100, 50, 50);
}
```

### 変数とは

手で計算するのではなく、もっとかしこくできないでしょうか? 描いた四角形の常に半分のサイズで次の四角形を描くには、現在のサイズの値を記録できると便利です。この「値を記録する」ために、変数を利用します。

変数とは、一時的に値（文字、文字列、数字など）を記憶しておく場所です。データを入れておく「箱」のようなものと考えてください。JavaScriptでは let を用いて変数を作ります。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="328" height="274" src="/wp-content/uploads/2026/10/03_slide12.png" alt="変数は値を入れておく箱" class="wp-image-19839" srcset="/wp-content/uploads/2026/10/03_slide12-300x251.png 300w, /wp-content/uploads/2026/10/03_slide12.png 328w" sizes="auto, (max-width: 328px) 100vw, 328px" /></figure>

変数は以下のように使います。

宣言 : 使用する変数の名前の箱を準備する

```javascript
let hoo;
```

代入 : 変数の箱に値を入れる

```javascript
let hoo = 0;
```

演算 : 変数の値を計算する

```javascript
hoo = hoo + 1;
```

### 変数を使って正方形を描く

先程の例は、変数を利用すると下記のようになります。

```javascript
function setup() {
  createCanvas(400, 400);
  let rectSize = 200;
  rect(100, 100, rectSize, rectSize);
  rectSize = rectSize / 2;
  rect(100, 100, rectSize, rectSize);
  rectSize = rectSize / 2;
  rect(100, 100, rectSize, rectSize);
  rectSize = rectSize / 2;
  rect(100, 100, rectSize, rectSize);
  rectSize = rectSize / 2;
  rect(100, 100, rectSize, rectSize);
  rectSize = rectSize / 2;
}
```

どんどん小さな正方形を描いていくことができました。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="480" height="502" src="/wp-content/uploads/2026/10/03_slide15.png" alt="どんどん小さくなる正方形" class="wp-image-19849" srcset="/wp-content/uploads/2026/10/03_slide15-287x300.png 287w, /wp-content/uploads/2026/10/03_slide15.png 480w" sizes="auto, (max-width: 480px) 100vw, 480px" /></figure>

### 変数の使用例

変数を利用して、いろいろ実験してみましょう。以下は、円の直径を少しずつ小さくしながら同心円を描く例です。

```javascript
function setup() {
  createCanvas(800, 600);
  background(0);
  noStroke();
  fill(0, 127, 255, 127);
  let x = width / 2;
  let y = height / 2;
  let diameter = height;
  ellipse(x, y, diameter, diameter);
  diameter = diameter / 1.4;
  ellipse(x, y, diameter, diameter);
  diameter = diameter / 1.4;
  ellipse(x, y, diameter, diameter);
  diameter = diameter / 1.4;
  ellipse(x, y, diameter, diameter);
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1600" height="1244" src="/wp-content/uploads/2026/10/03_slide18.png" alt="変数を使った同心円" class="wp-image-19844" srcset="/wp-content/uploads/2026/10/03_slide18-300x233.png 300w, /wp-content/uploads/2026/10/03_slide18-768x597.png 768w, /wp-content/uploads/2026/10/03_slide18-1024x796.png 1024w, /wp-content/uploads/2026/10/03_slide18-1536x1194.png 1536w, /wp-content/uploads/2026/10/03_slide18.png 1600w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

## 繰り返し

### 同じ命令のくりかえし

さっきのプログラムに注目してください。途中から同じ命令のくりかえしになっていないでしょうか?

```javascript
// ....
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
```

この繰り返しの部分を何度も書かずに、「以下の2行を10回くりかえし」のように一気に指定したいところです。

```javascript
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
```

### for文

そこで使用するのが for文です。for文は以下のように書きます。

```javascript
for (初期化式; 継続条件式; 再初期化式) {
  文;
}
```

- 初期化式 : 初期化の際の条件式
- 継続条件式 : 繰り返しを継続する条件式
- 再初期化式 : 繰り返されるたびに実行される式

同心円をくりかえしを用いて描画してみましょう。

```javascript
function setup() {
  createCanvas(800, 600);
  background(0);
  noStroke();
  fill(0, 127, 255, 63);
  let x = width / 2;
  let y = height / 2;
  let diameter = height;
  for (let i = 0; i < 100; i++) {
    ellipse(x, y, diameter, diameter);
    diameter = diameter / 1.4;
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1600" height="1244" src="/wp-content/uploads/2026/10/03_slide24.png" alt="くりかえしを用いた同心円" class="wp-image-19842" srcset="/wp-content/uploads/2026/10/03_slide24-300x233.png 300w, /wp-content/uploads/2026/10/03_slide24-768x597.png 768w, /wp-content/uploads/2026/10/03_slide24-1024x796.png 1024w, /wp-content/uploads/2026/10/03_slide24-1536x1194.png 1536w, /wp-content/uploads/2026/10/03_slide24.png 1600w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

### クイズ!! 入れ子状の形

for文を使用したくりかえしを用いた表現に挑戦してみましょう。入れ子状になった形を生成してみます!

**第1問 : 入れ子状の矩形**

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide26.png" alt="入れ子状の矩形" class="wp-image-19841" srcset="/wp-content/uploads/2026/10/03_slide26-300x253.png 300w, /wp-content/uploads/2026/10/03_slide26-768x648.png 768w, /wp-content/uploads/2026/10/03_slide26.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

ヒント : 下記のコードから開始してください。

```javascript
function setup() {
  createCanvas(800, 600);
  stroke(0);
  fill(0, 127, 255, 127);
  background(0);
  let x = 0;
  let y = 0;
  let w = width;
  let h = height;
}
```

解答例です。

```javascript
function setup() {
  createCanvas(800, 600);
  stroke(0);
  fill(0, 127, 255, 127);
  background(0);
  let x = 0;
  let y = 0;
  let w = width;
  let h = height;
  for (let i = 0; i < 32; i++) {
    rect(x, y, w, h);
    rect(x + w, y + h, w, h);
    w = w / 2;
    h = h / 2;
  }
}
```

**第2問 : 入れ子状の円**

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide29.png" alt="入れ子状の円" class="wp-image-19845" srcset="/wp-content/uploads/2026/10/03_slide29-300x253.png 300w, /wp-content/uploads/2026/10/03_slide29-768x648.png 768w, /wp-content/uploads/2026/10/03_slide29.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

ヒント : 下記のコードから開始してください。

```javascript
function setup() {
  createCanvas(800, 600);
  background(0);
  stroke(0);
  fill(0, 127, 255, 100);
  let x = width / 4;
  let y = height / 2;
  let diameter = width / 2;
}
```

解答例です。

```javascript
function setup() {
  createCanvas(800, 600);
  background(0);
  stroke(0);
  fill(0, 127, 255, 100);
  let x = width / 4;
  let y = height / 2;
  let diameter = width / 2;
  for (let i = 0; i < 32; i++) {
    ellipse(x, y, diameter, diameter);
    ellipse(x + diameter, y, diameter, diameter);
    diameter = diameter / 2;
    x = x / 2;
  }
}
```

### 応用 : 回転のくりかえし

translate() と rotate() を使って、図形を回転させながらくりかえし描いてみます。

```javascript
function setup() {
  createCanvas(800, 800);
  background(0);
  noStroke();
  fill(0, 127, 255, 30);
  let diameter = width / 1.8;
  translate(width / 2, height / 2);
  rotate(PI / 4);
  for (let i = 0; i < 256; i++) {
    ellipse(diameter / -2, 0, diameter, diameter);
    ellipse(diameter / 2, 0, diameter, diameter);
    diameter = diameter / 1.05;
    rotate(PI / 24.0);
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1630" height="1666" src="/wp-content/uploads/2026/10/03_slide33.png" alt="回転のくりかえし" class="wp-image-19848" srcset="/wp-content/uploads/2026/10/03_slide33-294x300.png 294w, /wp-content/uploads/2026/10/03_slide33-768x785.png 768w, /wp-content/uploads/2026/10/03_slide33-1002x1024.png 1002w, /wp-content/uploads/2026/10/03_slide33-1503x1536.png 1503w, /wp-content/uploads/2026/10/03_slide33.png 1630w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

## 乱数

プログラムは、設定された手続きを何度でも繰り返します。そのままでは、予想外の挙動はしません。完全に全てをコントロールするのではなく、偶然性、意外性をとり入れたいときに使うのが、実行する度に毎回異なる値を出力する仕組み「乱数」です。乱数は、何ら法則性、規則性のない、でたらめな値 (ランダムな値) を出力します。

p5.jsでは random() 関数で乱数を生成します。引数で乱数の範囲を指定します。

例 : 0から100の乱数を生成

```javascript
random(100);
```

例 : 100から1000の乱数を生成

```javascript
random(100, 1000);
```

## 乱数と繰り返し

乱数 (random) と繰り返し (for) を使用して、表現してみましょう! ここからは、自由な発想でクリエイティブに!

### たくさんの円を描く

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noStroke();
  for (let i = 0; i < 100; i++) {
    fill(random(0, 127), random(0, 255), random(127, 255), 127);
    circle(random(width), random(height), random(10, 100));
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide40.png" alt="たくさんの円" class="wp-image-19846" srcset="/wp-content/uploads/2026/10/03_slide40-300x253.png 300w, /wp-content/uploads/2026/10/03_slide40-768x648.png 768w, /wp-content/uploads/2026/10/03_slide40.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

### たくさんの矩形を描く

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noStroke();
  rectMode(CENTER);
  for (let i = 0; i < 100; i++) {
    fill(random(127, 255), random(0, 127), random(0, 127), 127);
    rect(random(width), random(height), random(10, 200), random(10, 200));
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide42.png" alt="たくさんの矩形" class="wp-image-19850" srcset="/wp-content/uploads/2026/10/03_slide42-300x253.png 300w, /wp-content/uploads/2026/10/03_slide42-768x648.png 768w, /wp-content/uploads/2026/10/03_slide42.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

### 座標の情報を取り入れる

円の大きさに y座標を適用してみます。map() 関数を使って、y座標 (0〜height) を直径 (80〜10) に変換しています。

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noStroke();
  for (let i = 0; i < 1000; i++) {
    let x = random(width);
    let y = random(height);
    let diameter = map(y, 0, height, 80, 10);
    fill(random(0, 127), random(0, 255), random(127, 255), 127);
    circle(x, y, diameter);
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide44.png" alt="大きさにy座標を適用" class="wp-image-19852" srcset="/wp-content/uploads/2026/10/03_slide44-300x253.png 300w, /wp-content/uploads/2026/10/03_slide44-768x648.png 768w, /wp-content/uploads/2026/10/03_slide44.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

### 2種類の図形を組み合わせる

画面の左半分に円、右半分に矩形を描いてみます。

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noStroke();
  rectMode(CENTER);
  for (let i = 0; i < 1000; i++) {
    let x = random(width / 2);
    let y = random(height);
    let diameter = random(y / 10.0);
    fill(random(0, 127), random(0, 255), random(127, 255), 127);
    ellipse(x, y, diameter, diameter);
  }
  for (let i = 0; i < 1000; i++) {
    let x = random(width / 2) + width / 2;
    let y = random(height);
    let diameter = random((height - y) / 10.0);
    fill(random(127, 255), random(0, 255), random(0, 31), 127);
    rect(x, y, diameter, diameter);
  }
}
```

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="675" src="/wp-content/uploads/2026/10/03_slide46-1.png" alt="2種類の図形を組み合わせる" class="wp-image-19851" srcset="/wp-content/uploads/2026/10/03_slide46-1-300x253.png 300w, /wp-content/uploads/2026/10/03_slide46-1-768x648.png 768w, /wp-content/uploads/2026/10/03_slide46-1.png 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

## 関連リンク

- [p5.js Web Editor](https://editor.p5js.org/)
- [p5.js リファレンス](https://p5js.org/reference/)
- [p5.js リファレンス: for](https://p5js.org/reference/p5/for/)
- [p5.js リファレンス: let](https://p5js.org/reference/p5/let/)
- [p5.js リファレンス: random()](https://p5js.org/reference/p5/random/)
- [p5.js リファレンス: map()](https://p5js.org/reference/p5/map/)
- [OpenProcessing](https://www.openprocessing.org/)

## 本日の課題

テーマ: 「乱数 (random) と繰り返し (for) を使用した表現」

今回学んだ乱数 (random) と繰り返し (for) を使用して、自由な発想で表現してみましょう! 次回の授業の冒頭で簡単に作品をいくつか紹介します。

- 完成した作品には、タイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出
- 必ず TAGS: [sfc261016](https://openprocessing.org/browse?q=sfc261016&time=anytime&type=tags&offset=0#) を入れてください
- 提出期限 10/22/2026

[課題提出フォーム](https://docs.google.com/forms/d/e/1FAIpQLSfhS3oIn2oNGNT-FwfUjKQLMedSXPpvTeUc80qJsDx341hINg/viewform?usp=publish-editor)
