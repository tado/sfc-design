![100個の円が同時に動く](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide35.png)

今回は、p5.jsで「動き」を生みだす方法について学びます。

まず始めに、アニメーションの基本となる setup() と draw() による構造化について解説します。draw() がくりかえし実行される仕組みを使って、図形の場所や色を少しずつ変化させることで、アニメーションをつくります。

次に、前回学んだ変数に加えて「条件分岐 (if文)」を使い、画面の端でバウンドする動きを実現します。さらに、位置や速度を「ベクトル (p5.Vector)」として扱うことで、動きの定義をより整理して書き直します。

最後に、「配列」とfor文を組み合わせて、たくさんの図形を同時に動かしてみましょう。

## スライド資料

<!-- スライド資料へのリンクを追加 -->
[スライド資料: 動きを生みだす - アニメーションとベクトル](URL)

## 今日の内容

- アニメーション (setup と draw)
- 増殖する円
- 条件分岐 + アニメーション
- ベクトル (向きと大きさ) で動きを再定義
- たくさんの図形を同時に動かす (配列)
- 実習

## アニメーション

### パラパラ漫画のしくみ

アニメーションをつくるには、すこしづつ変化する画像を、一定間隔で入れ替える必要があります。パラパラ漫画と同じしくみです。

p5.jsでアニメーションを実現するには、これまでのプログラムをより構造化していく必要があります。

### setup() と draw()

p5.jsでは、プログラムを setup() と draw() という二つのパートに構造化してアニメーションを実現します。

- setup() - 初期設定 : プログラムの起動時に一度だけ実行されます。画面の基本設定やフレームレートなどを設定します。
- draw() - 描画 : 設定した速さ (フレームレート) で、プログラムが終了するまでくりかえし実行されます。

![setup()とdraw()のイメージ](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide04.svg)

setup() は初期化関数です。プログラムの最初に1回だけ実行される処理、つまりアニメーションの前準備を記述します。setup() の中では、以下のような処理を行うことが多いです。

- createCanvas() : 画面のサイズを設定
- frameRate() : 画面の書き換え速度を設定
- colorMode() : カラーモードを設定

draw() はメインループ関数です。プログラムが終了するまでくりかえし実行されます。このループの中で図形の場所や色、形を操作してアニメーションにします。画面の書き換え頻度は frameRate() 関数で設定します。

この構造をp5.jsで記述すると、以下のようになります。これ以降のプログラムで共通する枠組みです。

```javascript
// 全体に共通する変数の宣言
function setup() {
  // 初期設定
}
function draw() {
  // 描画
}
```

## 増殖する円

この setup() → draw() の構造を実感してみましょう。draw() が実行されるたびに、ランダムな場所に円 (circle) を描画してみます。

```javascript
//初期化関数
function setup() {
  createCanvas(windowWidth, windowHeight);
  frameRate(12);   //書き換え頻度の設定
  background(0);
}
//メインループ
function draw() {
  noStroke();
  fill(random(255), random(255), random(255));
  circle(random(width), random(height), random(100));
}
```

background() を setup() の中で1回だけ実行しているため、draw() で描いた円は消されずに残り、どんどん増殖していきます。

![増殖する円](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide10.jpg)

## アニメーション入門

### アニメーション作成の考えかた

アニメーションは、以下のような考えかたで作成します。

- setup() 関数で全体に共通の設定を初期化
- draw() 関数を繰り返す
  - 背景の描画
  - 図形を描く
  - パラメータ (場所、色など) を微妙に変更

### 円の移動

この仕組みを利用して、円が斜め下に移動するプログラムを作成してみましょう。円の位置 (locX, locY) と速度 (velX, velY) を変数として宣言し、draw() が実行されるたびに位置に速度を足していきます。

```javascript
let locX, locY; //円の中心位置を格納する変数
let velX, velY; //円の速度を格納する変数

function setup() {
  createCanvas(windowWidth, windowHeight); //画面を生成
  frameRate(60); //フレームレート
  locX = 0; //円の初期位置X
  locY = 0; //円の初期位置Y
  velX = 3; //円の初期速度X
  velY = 2; //円の初期速度Y
}

function draw() {
  background(0); //背景を描画
  locX = locX + velX; //円のX座標を更新
  locY = locY + velY; //円のY座標を更新
  noStroke(); //枠線なし
  fill(0, 127, 255); //塗りの色
  circle(locX, locY, 20); //指定した位置に円を描画
}
```

今度は draw() の最初で毎回 background() を描画しているので、前のフレームの円は消え、円が等速度で移動するように見えます。

![円が等速度で移動する](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide13.jpg)

アニメーションで変化させるパラメータは、座標だけではありません。色をアニメーションすることも可能です。例えば、fill() の値を変化させれば、色が徐々に変化していきます。

## 条件分岐 + アニメーション

### 画面の端でバウンドさせる

先程のプログラムでは、円は画面の外に出ていってしまいました。そこで、画面の端にきたらバウンドする動きを加えてみましょう。

バウンドを表現するには、x方向とy方向のスピードはどうなれば良いでしょうか?

![バウンドする動き](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide17.svg)

この動きを実現するには、以下の条件を設定する必要があります。

- 画面の右端、もしくは画面の左端 → X方向のスピードを反転
- 画面の上端、もしくは画面の下端 → Y方向のスピードを反転

### 条件分岐の構文

「もし○○したら、××せよ」という処理を書くには、条件分岐 (if文) を使います。条件分岐の構文は以下のようになります。

```
if ([条件式]) {
  [条件が正しい場合の処理]
} else {
  [条件が誤っている場合の処理]
}
```

この条件分岐を、先程の円の動きに適用します。

- 条件1 : もし左右の端に来たら、X座標方向の速度を反転
- 条件2 : もし上下の端に来たら、Y座標方向の速度を反転

速度に -1 をかけると、向きが反転します。また、条件式の中の *||* は「または」という意味です。

```javascript
let locX, locY; //円の中心位置を格納する変数
let velX, velY; //円の速度を格納する変数

function setup() {
  createCanvas(windowWidth, windowHeight); //画面を生成
  frameRate(60); //フレームレート
  locX = width / 2; //円の初期位置X
  locY = height / 2; //円の初期位置Y
  velX = random(-10, 10); //円の初期速度X
  velY = random(-10, 10); //円の初期速度Y
}

function draw() {
  background(0); //背景を描画
  locX = locX + velX; //円のX座標を更新
  locY = locY + velY; //円のY座標を更新
  noStroke(); //枠線なし
  fill(0, 127, 255); //塗りの色
  circle(locX, locY, 20); //指定した位置に円を描画
  //バウンド
  if (locX < 0 || locX > width) { //もし画面の左端、または右端に到達したら
    velX = velX * -1; //X方向のスピードを反転
  }
  if (locY < 0 || locY > height) { //もし画面の下端、または上端に到達したら
    velY = velY * -1; //Y方向のスピードを反転
  }
}
```

画面の端でバウンドする動きになりました!

![画面の端でバウンドする](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide13.jpg)

## ベクトル (向きと大きさ) で動きを再定義

### ベクトルとは

ここまでの動きの定義の方法は、あまり洗練されたやり方ではありませんでした。

- 位置 : locX と locY
- 速度 : velX と velY

それぞれのパラメーターで、常に (x, y) という2つの変数を使っています。もっと整理して定義できないでしょうか? そこで「ベクトル」という概念を導入します。

ベクトル (vector) とは、幾何学的空間における、大きさと向きを持った量です。例えば、速度、加速度、力などがベクトルで表されます。平面上や空間内の矢印としてイメージしてください。

![ベクトルのイメージ](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide25.png)

例えば、原点 (0, 0) から (2, 3) の座標までのベクトルは以下のようになります。

![原点(0,0)から(2,3)までのベクトル](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide26.png)

### p5.Vector

p5.jsには、ベクトルを定義するのに適した「p5.Vector」というクラス (属性と動作の型) が用意されています。2次元平面でのアニメーションは、p5.Vectorクラスを用いることでとても簡単に整理されます。

画面の端でバウンドするアニメーションを、p5.Vectorを使用して書き直してみましょう。createVector() でベクトルを生成し、add() で位置ベクトルに速度ベクトルを足します。ベクトルのx成分、y成分は、それぞれ *.x*、*.y* で取り出せます。

```javascript
let loc; //円の中心の位置ベクトル
let vel; //円の速度ベクトル

function setup() {
  createCanvas(windowWidth, windowHeight); //画面を生成
  frameRate(60); //フレームレート
  loc = createVector(width / 2, height / 2);
  vel = createVector(random(-10, 10), random(-10, 10));
}

function draw() {
  background(0); //背景を描画
  loc.add(vel); //円の座標を更新
  noStroke(); //枠線なし
  fill(0, 127, 255); //塗りの色
  circle(loc.x, loc.y, 20); //指定した位置に円を描画
  //バウンド
  if (loc.x < 0 || loc.x > width) { //もし画面の左端、または右端に到達したら
    vel.x = vel.x * -1; //X方向のスピードを反転
  }
  if (loc.y < 0 || loc.y > height) { //もし画面の下端、または上端に到達したら
    vel.y = vel.y * -1; //Y方向のスピードを反転
  }
}
```

## たくさんの図形を同時に動かす

### 配列

たくさんの図形を同時に動かすには、どうすれば良いでしょうか? 図形の数だけ同じコードを書くと、動かす図形が100個、1000個と増えるにつれ破綻してしまいます。こうした際には、「配列」を使うと良いでしょう。

配列は、データのロッカーのようなイメージです。1つの名前で複数の値を格納し、番号 (インデックス) で取り出します。番号は0から始まります。

```javascript
let data = [];
```

![配列のイメージ](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide31.png)

### 配列で位置と速度を管理する

位置 (location)、速度 (velocity) をそれぞれ配列に変更して、沢山の位置と速度を扱えるようにしてみましょう。配列と、前回学んだくりかえしの構文 (for文) を組み合わせます。

```javascript
const NUM = 100; //円の数
let loc = []; //円の中心の位置ベクトル
let vel = []; //円の速度ベクトル

function setup() {
  createCanvas(windowWidth, windowHeight); //画面を生成
  frameRate(60); //フレームレート
  for (let i = 0; i < NUM; i++) {
    loc[i] = createVector(width / 2, height / 2);
    vel[i] = createVector(random(-10, 10), random(-10, 10));
  }
}

function draw() {
  background(0); //背景を描画
  noStroke(); //枠線なし
  fill(0, 127, 255); //塗りの色
  //円の数だけくりかえす
  for (let i = 0; i < NUM; i++) {
    loc[i].add(vel[i]); //円の座標を更新
    circle(loc[i].x, loc[i].y, 20); //指定した位置に円を描画
    if (loc[i].x < 0 || loc[i].x > width) { //もし画面の左端、または右端に到達したら
      vel[i].x = vel[i].x * -1; //X方向のスピードを反転
    }
    if (loc[i].y < 0 || loc[i].y > height) { //もし画面の下端、または上端に到達したら
      vel[i].y = vel[i].y * -1; //Y方向のスピードを反転
    }
  }
}
```

100個の円が、同時に動きます!

![100個の円が同時に動く](https://raw.githubusercontent.com/tado/sfc-design/main/img/04_slide35.png)

## 関連リンク

- [p5.js Web Editor](https://editor.p5js.org/)
- [p5.js リファレンス](https://p5js.org/reference/)
- [p5.js リファレンス: setup()](https://p5js.org/reference/p5/setup/)
- [p5.js リファレンス: draw()](https://p5js.org/reference/p5/draw/)
- [p5.js リファレンス: frameRate()](https://p5js.org/reference/p5/frameRate/)
- [p5.js リファレンス: if](https://p5js.org/reference/p5/if/)
- [p5.js リファレンス: createVector()](https://p5js.org/reference/p5/createVector/)
- [p5.js リファレンス: p5.Vector](https://p5js.org/reference/p5/p5.Vector/)
- [p5.js リファレンス: Array](https://p5js.org/reference/p5/Array/)
- [OpenProcessing](https://www.openprocessing.org/)

## 本日の課題

テーマ: 「アニメーションにランダムな要素を追加する」

本日の最終のコード (たくさんの図形を同時に動かす) を改造して、ランダムな要素を追加してみましょう! 次回の授業の冒頭で簡単に作品をいくつか紹介します。

例えば、以下のような改造が考えられます。

- 円の色をランダムな色に
- 円の大きさをランダムに
- (応用) 円の動きをランダムに

提出方法は以下の通りです。

- 完成した作品には、タイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出
- 必ず TAGS: sfc261023 を入れてください
- 前回の[提出作品](https://openprocessing.org/browse?q=sfc261016&time=anytime&type=tags&offset=0)で良いと思った作品を1つ選んでください
- 提出期限 10/29/2026

<!-- 提出フォームのURLを追加 -->
[課題提出フォーム](https://docs.google.com/forms/d/e/1FAIpQLSeXX3Senkm_D5kG7B6liuZtPiXVZz1V6m6Ep6wxz-97y60_lQ/viewform?usp=publish-editor)

### 参考作品

円の大きさと色をランダムにした例です。円の大きさ (sizes) と色 (colors) も配列で管理しています。また、円の半径を考慮して、円が画面の端からはみ出さずにバウンドするようにしています。

```javascript
const NUM = 100; //円の数
let loc = []; //円の中心の位置ベクトル
let vel = []; //円の速度ベクトル
let sizes = []; //円の大きさ
let colors = []; //円の色

function setup() {
  createCanvas(windowWidth, windowHeight); //画面を生成
  frameRate(60); //フレームレート
  for (let i = 0; i < NUM; i++) {
    loc[i] = createVector(width / 2, height / 2);
    vel[i] = createVector(random(-10, 10), random(-10, 10));
    sizes[i] = random(10, 50);
    colors[i] = color(random(255), random(255), random(255));
  }
}

function draw() {
  background(0); //背景を描画
  noStroke(); //枠線なし
  //円の数だけくりかえす
  for (let i = 0; i < NUM; i++) {
    const radius = sizes[i] / 2;
    loc[i].add(vel[i]); //円の座標を更新

    //もし画面の左端、または右端に到達したら
    if (loc[i].x < radius || loc[i].x > width - radius) {
      loc[i].x = constrain(loc[i].x, radius, width - radius);
      vel[i].x = vel[i].x * -1; //X方向のスピードを反転
    }

    //もし画面の下端、または上端に到達したら
    if (loc[i].y < radius || loc[i].y > height - radius) {
      loc[i].y = constrain(loc[i].y, radius, height - radius);
      vel[i].y = vel[i].y * -1; //Y方向のスピードを反転
    }

    fill(colors[i]);
    circle(loc[i].x, loc[i].y, sizes[i]);
  }
}
```
