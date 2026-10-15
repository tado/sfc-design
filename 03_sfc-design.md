---
marp: true
theme: tadokoro
paginate: true
---

# デザインとプログラミング 2026<br>反復と乱数

慶應義塾大学環境情報学部
田所 淳

---

<!-- _class: bigtxt -->

# 反復 (Iteration)

---

## 反復 (Iteration)

- コンピューターは、「くりかえし」の天才!
- 最近のマシンであれば、1秒間に20億回（2GHz）以上のクロックで、正確に計算をくりかえすことができる
- 反復は、プログラムの基本的で重要な構造のひとつ

![height:340](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide03.png)

---

## 反復 (Iteration)

- 構造化プログラミング、3つの構成要素
- 順次実行 (Sequence)、分岐 (Selection)、反復 (Iteration)

![height:400](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide04.svg)

---

## 反復 (Iteration)

- すべてのアルゴリズムが3つの基本的な制御構造を使用して表現できる
- 構造化定理

1. 順次実行（Sequence）: 命令は上から下へと順番に実行される
2. 選択（Selection）: 条件分岐、「もし○○なら××しなさい、そうでなければ△△しなさい」
3. 反復（Iteration）: 繰り返し → **本日の主題**

---

<!-- _class: bigtxt -->

# 変数

---

## 変数

- クイズ：
- 正方形の中に、ちょうど半分の幅と高さの正方形を描く

![height:400](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide07.png)

---

## 変数

- 答え

```javascript
function setup() {
  createCanvas(400, 400);
  rect(100, 100, 200, 200);
  rect(100, 100, 100, 100);
}
```

---

## 変数

- クイズ2：
- さらに半分の正方形を中に

![height:400](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide09.png)

---

## 変数

- 答え

```javascript
function setup() {
  createCanvas(400, 400);
  rect(100, 100, 200, 200);
  rect(100, 100, 100, 100);
  rect(100, 100, 50, 50);
}
```

---

## 変数

- 手で計算するのではなく、もっとかしこくできないか
- 描いた四角形の常に半分のサイズで次の四角形を描く
- 現在のサイズの値を記録できると便利なのに…
- ↓
- **「値を記録する」→ 変数を利用する**

---

## 変数

- 変数とは?
  - 一時的に値（文字、文字列、数字など）を記憶しておく場所
  - データを入れておく「箱」のようなもの
- JavaScriptでは let を用いる

![height:260](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide12.png)

---

## 変数

- 宣言：使用する変数の名前の箱を準備する

```javascript
let hoo;
```

- 代入：変数の箱に値を入れる

```javascript
let hoo = 0;
```

- 演算：変数の値を計算する

```javascript
hoo = hoo + 1;
```

---

## 変数

- 先程の例は、変数を利用すると下記のようになる

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

---

## 変数

- どんどん小さな正方形を描いていくことができる

![height:400](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide15.png)

---

## 変数

- 変数を利用して、いろいろ実験してみましょう

---

## 変数

- 変数の使用例

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

---

## 変数

![height:460](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide18.png)

---

<!-- _class: bigtxt -->

# 繰り返し

---

## 繰り返し

- さっきのプログラムに注目
- 途中から同じ命令のくりかえしになっていないだろうか?
- たとえば最初の例

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

---

## 繰り返し

- 繰り返しの部分を何度も書かずに一気に指定したい

```javascript
diameter = diameter / 1.4;
ellipse(x, y, diameter, diameter);
```

- ↓
- **これを10回くりかえし**

---

## 繰り返し

- for文の書きかた

```
for (初期化式; 継続条件式; 再初期化式) {
  文;
}
```

- 初期化式：初期化の際の条件式
- 継続条件式：繰り返しを継続する条件式
- 再初期化式：繰り返されるたびに実行される式

---

## 繰り返し

- 同心円をくりかえしを用いて描画

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

---

## 繰り返し

- 同心円をくりかえしを用いて描画

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide24.png)

---

## クイズ!!

- for文を使用したくりかえしを用いた表現
- 入れ子状になった形を生成してみる!

---

## 繰り返し

- 第1問 : 入れ子状の矩形

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide26.png)

---

## 繰り返し

- ヒント : 下記のコードから開始

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

---

## 繰り返し

- 解答

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

---

## 繰り返し

- 第2問!! 入れ子状の円

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide29.png)

---

## 繰り返し

- ヒント - 入れ子状の円

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

---

## 繰り返し

- 解答

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

---

## 繰り返し

- 応用: 回転のくりかえし

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

---

## 繰り返し

![height:460](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide33.png)

---

<!-- _class: bigtxt -->

# 乱数

---

## 乱数

- プログラムは、設定された手続きを何度でも繰り返す
- そのままでは、予想外の挙動はしない
- 完全に全てをコントロールするのではなく、偶然性、意外性をとり入れたい
- 実行する度に毎回異なる値を出力する仕組み
- 乱数
  - 何ら法則性、規則性のない、でたらめな値を出力
  - ランダム

---

## 乱数

- p5.jsで乱数を生成 - 乱数の範囲を指定する
- 例：0から100の乱数を生成

```javascript
random(100);
```

- 例：100から1000の乱数を生成

```javascript
random(100, 1000);
```

---

<!-- _class: bigtxt -->

# 乱数と繰り返し

---

## 乱数と繰り返し

- 乱数 (random) と繰り返し (for) を使用して、表現してみる!
- ここからは、自由な発想でクリエイティブに!

---

## 乱数と繰り返し

- 例：たくさんの円を描く

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

---

## 乱数と繰り返し

- 例：たくさんの円を描く

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide40.png)

---

## 乱数と繰り返し

- 例：たくさんの矩形

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

---

## 乱数と繰り返し

- 例：たくさんの矩形

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide42.png)

---

## 乱数と繰り返し

- 座標の情報を取り入れる - 大きさにy座標を適用

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

---

## 乱数と繰り返し

- 座標の情報を取り入れる - 大きさにy座標を適用

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide44.png)

---

## 乱数と繰り返し

- 2種類の図形を組み合わせてみる

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

---

## 乱数と繰り返し

- 2種類の図形を組み合わせてみる

![height:420](https://raw.githubusercontent.com/tado/sfc-design/main/img/03_slide46.png)

---

<!-- _class: bigtxt -->

# 本日の課題!!

---

## 本日の課題!!

- 乱数 (random) と繰り返し (for) を使用して、表現してみる!
  - OpenProcessingに投稿
  - 完成した作品には、タイトルをつける
  - 投稿したURLをアンケートから提出
  - TAGS: sfc261016 を必ずつけること
  - 前回の[提出作品](https://openprocessing.org/browse?q=sfc261009&time=anytime&type=tags&offset=0)で良いと思った作品を1つ選んでください
