# かたちとコード / 基本図形と色彩による画面構成

![p5.jsで描いた基本図形と色](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide40.svg)

この講義では、p5.jsを使用してコードによるデザインを行います。その最初の一歩として、コードによって「かたち」を描くにはどうすれば良いのか考えていきます。

まず始めに、p5.jsで実際に図形を描いていきます。p5.jsの操作の基本を解説し、簡単な図形を描きながらp5.jsでのプログラミングの基本を学びます。

最後に、1960年代〜70年代の、コンピューター黎明期から発展期におけるコード（プログラム）による様々な視覚表現について紹介します。過去の作家がどのようなアイデアで、何を表現しようとしてきたのか、その歴史を辿ります。

## スライド資料

<!-- スライド資料へのリンクを追加 -->
[スライド資料: かたちとコード / 基本図形と色彩による画面構成](https://drive.google.com/file/d/1Q6pCgT5w0O9r3yAqDOSB-H2LLy11o8gW/view?usp=sharing)

## 今日の内容

- 「かたちとコード」について
- p5.js入門
- 座標について
- 形を描いてみる
- 実習

## かたちとコード

コード（プログラミング）で形を描くことには、どのような意味があるのでしょうか? また、どのような表現に向いているのでしょうか?

- **正確** : 指定した通りに寸分違わず形を描くことができる
- **反復** : 何度でも同じ操作をくりかえす
- **論理（アルゴリズム）** : 形を描くルール自体を書くことができる

コンピューターの登場黎明期から、こうした特徴を活かした様々な表現が行われてきました。

## p5.jsはじめの一歩

### p5.js Web Editor

p5.jsを始める一番簡単な方法は、p5.js Web Editorを使う方法です。今日はこれで進めていきます!

- [https://editor.p5js.org/](https://editor.p5js.org/)

![p5.js Web Editor](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide04.png)

操作は簡単です!!

- 実行(Run)ボタン：プログラムの実行
- 停止(Stop)ボタン：プログラムの停止

![実行ボタンと停止ボタン](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide05.jpg)

p5.jsを起動した段階で、既にプログラムのテンプレートが入っています!

```javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```

### setup() と draw()

では、function setup() と function draw() は何なのでしょうか? これはアニメーションを実現する仕組みです。すこしずつ変化する画像を一定間隔で入れ替えている、パラパラ漫画をイメージしてください。

p5.jsでは、setup()とdraw()という二つのパートに構造化してアニメーションを実現しています。

- **setup() - 初期設定** : プログラムの起動時に一度だけ実行されます。画面の基本設定やフレームレートなどを設定します。
- **draw() - 描画** : 設定した速さ(フレームレート)でプログラムが終了するまでくりかえし実行されます。

![setup()とdraw() のイメージ](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide09.svg)

setup (初期化関数) には、プログラムの最初に1回だけ実行される処理、つまりアニメーションの前準備を記述します。setupの中で行われることの多い処理は以下のとおりです。

- createCanvas：画面のサイズを設定
- frameRate：画面の書き換え速度を設定
- colorMode：カラーモードを設定

draw (メインループ関数) は、プログラムが終了するまでくりかえし実行されます。ループの中で図形の場所や色、形を操作してアニメーションにします。画面の書き換え頻度はframeRate()関数で設定します。

### プログラムの書き方の基本

- 実行の順序：上から順番に読みこまれていく
- 半角の英数字 (全角はダメ) のみを使用すること
- 文末にはセミコロン “;” を入れる
- いろいろな括弧が入れ子構造になっている
- おなじ括弧に囲まれている部分がひとつのブロック
- 最小単位 → 関数 : `関数名(引数);`

### 関数

関数 (function) とは、引数と呼ばれるデータを受け取り、定められた通りの処理を実行して結果を返す一連の命令群です。

p5.jsは、ビジュアルプログラミングのための関数の集合です。関数は関数名とその引数（パラメータ）から構成されていて、引数の数は関数によって異なります。

```
関数名(引数1, 引数2, 引数3...);
```

## コンピュータで絵を描くということ

### ピクセル

コンピュータの画面はどうなっているのでしょうか? コンピュータの画面を拡大していくと、縦横に並んだ点の集合であることがわかります。この点をピクセル (Pixel) と呼びます。一つのピクセルは赤、緑、青の三原色から成り立っています。

![コンピュータの画面を拡大したところ](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide14.png)

コンピュータ画面は、縦横沢山のピクセルから構成された巨大なエクセルの表のようなものです。例えば 1024 x 768 の液晶画面は、横に1024列、縦に768行ならんだ巨大な表で、それぞれのセルにR,G,B,A(アルファ値)が格納されています。

![ピクセルとR, G, B, A](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide15.svg)

### 座標

座標 (Coordinate) とは、点の位置を明確にするために与えられる数の組のことです。

コンピュータの画面の1点を指定するためには、いくつのパラメータが必要でしょうか? 答えは2つの数字 (横と縦) : (x, y) です。これは2次元平面における直交座標です。

p5.js (Processing) の座標系は以下のようになっています。

- 左上が原点 (0, 0)
- 右に行くほどx座標の値が増える
- 下に行くほどy座標の値が増える

例：100 x 100の平面の座標系

![p5.jsの座標系](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide17.svg)

## 形を描いてみる

### キャンバスを用意する

まず、形を描いていく画面 (キャンバス) を用意します。createCanvas関数でキャンバスの大きさを指定します。

```
createCanvas(<幅>, <高さ>);
```

例：幅320pixel, 高さ240pixelのキャンバスを用意する

```javascript
createCanvas(320, 240);
```

### コメント

プログラムにコメントを入れることで、分かり易くなります。

```javascript
//一行だけのコメント

/*
 複数の行にまたがる
 コメント
 */
```

### 点を描く

point関数で点を描きます。

```
point(<X座標>, <Y座標>);
```

例：X座標100, Y座標120の位置に点を描く

```javascript
point(100, 120);
```

![point関数](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide21.svg)

### 直線を描く

line関数で直線を描きます。

```
line(<X座標始点>, <Y座標始点>, <X座標終点>, <Y座標終点>);
```

例：

```javascript
line(10, 10, 200, 180);
```

![line関数](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide23.svg)

### 長方形を描く

rect関数で長方形を描きます。

```
rect(<X座標>, <Y座標>, <長方形の幅>, <長方形の高さ>);
```

例：

```javascript
rect(10, 10, 200, 180);
```

![rect関数](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide25.svg)

### 楕円を描く

ellipse関数で円、楕円を描きます。

```
ellipse(<X座標>, <Y座標>, <楕円の幅>, <楕円の高さ>);
```

例：

```javascript
ellipse(10, 10, 200, 180);
```

![ellipse関数](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide27.svg)

### 基本図形を描く

ここまで出てきた基本図形を描いてみましょう。

```javascript
function setup() {
  createCanvas(800, 600);
}

function draw() {
  background(220);
  point(100, 200); // 点を描画
  line(80, 40, 700, 500); // 線を描画
  rect(200, 300, 400, 200); // 四角形を描画
  ellipse(500, 300, 300, 200); // 楕円を描画
}
```

できた!

![基本図形を描いた結果](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide29.svg)

## 色の指定

色を指定するには、R(赤) G(緑) B(青)の三原色で指定します。これは加法混色、つまり光の三原色であることに注意してください (絵の具などの色料の三原色とは異なります)。

![光の三原色 (加法混色)](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide30a.svg)

![色料の三原色 (減法混色)](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide30b.svg)

### 3つの色の属性

背景色 : background関数

```
background(<Rの値>, <Gの値>, <Bの値>);
```

線に色をつける : stroke関数

```
stroke(<Rの値>, <Gの値>, <Bの値>);
```

塗りの色をつける : fill関数

```
fill(<Rの値>, <Gの値>, <Bの値>);
```

### 色の塗りかたの規則

- 色や線塗りつぶしの設定は、それ以降すべての描画に使われる
- 色を変えるには改めて別の色を設定する命令を入れる

背景色、塗りつぶしの色、ストロークの色の指定の例です。

```javascript
//背景色
background(128); //グレースケールで指定
//塗りつぶしの色
fill(128, 64, 32); //RGB
//線の色
stroke(128, 64, 32); //RGB
```

さきほど描いた図形に色を塗ってみましょう。

```javascript
function setup() {
  createCanvas(800, 600);
}

function draw() {
  background(0); // 背景色
  stroke(255, 255, 31); //線の色
  fill(31, 127, 255); //塗り潰しの色
  point(100, 200); // 点を描画
  line(80, 40, 700, 500); // 線を描画
  rect(200, 300, 400, 200); // 四角形を描画
  ellipse(500, 300, 300, 200); // 楕円を描画
}
```

線と塗りの色が反映されます。

![色を塗った結果](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide35.svg)

### 透明度

R, G, Bの3つの値に続けて、もう1つ値を指定すると、透明度を意味します。

背景色

```
background(<Rの値>, <Gの値>, <Bの値>, <透明度>);
```

線

```
stroke(<Rの値>, <Gの値>, <Bの値>, <透明度>);
```

塗り

```
fill(<Rの値>, <Gの値>, <Bの値>, <透明度>);
```

先程の例に透明度を付加してみます。

```javascript
function setup() {
  createCanvas(800, 600);
}

function draw() {
  background(0); // 背景色
  stroke(255, 255, 31); //線の色
  fill(31, 127, 255, 127); //塗り潰しの色(半透明)
  point(100, 200); // 点を描画
  line(80, 40, 700, 500); // 線を描画
  rect(200, 300, 400, 200); // 四角形を描画
  ellipse(500, 300, 300, 200); // 楕円を描画
}
```

透明度が付加されます。

![透明度を付加した結果](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide38.svg)

### 色の塗り分け

複数の色を塗り分けてみましょう。図形を描く前に、その都度 fill() で色を指定します。

```javascript
function setup() {
  createCanvas(800, 600);
}

function draw() {
  background(0); // 背景色
  stroke(255, 255, 31); // 線の色
  point(100, 200); // 点を描画
  line(80, 40, 700, 500); // 線を描画
  fill(31, 127, 255, 127); // 四角形の色
  rect(200, 300, 400, 200); // 四角形を描画
  fill(255, 127, 31, 127);  // 楕円の色
  ellipse(500, 300, 300, 200); // 楕円を描画
}
```

色を塗り分けることができました。

![色を塗り分けた結果](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide40.svg)

## OpenProcessingにアカウントを作成してコードをシェア

[OpenProcessing](https://www.openprocessing.org/) は、p5.jsのコードをシェアできるサービスです。無料で利用可能です (有料オプションもあり)。早速登録してみましょう! トップページの「Join」ボタンから登録できます。

![OpenProcessing](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide42.png)

作成したコードをシェアする手順は動画で紹介します! とっても簡単です!!

## 関連リンク

- [p5.js Web Editor](https://editor.p5js.org/)
- [p5.js リファレンス](https://p5js.org/reference/)
- [OpenProcessing](https://www.openprocessing.org/)
- [Spacewar! (ブラウザ版)](https://www.masswerk.at/spacewar/)
- [Casey Reas](http://reas.com/)
- [Process Compendium 2004-2010 (Vimeo)](https://vimeo.com/22955812)

## 本日の課題

テーマ: 「p5.js基本図形と色による画面構成」

ここまで解説したp5.jsの機能を活用して画面構成をしてみましょう! 座標、色、数値による図形の描画に慣れるのが目的です。次回の授業の冒頭で簡単に作品をいくつか紹介します。

- 完成したら何かタイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出

<!-- 投稿時のタグ、提出締切、提出フォームのURLを追加 -->

## 過去へタイムスリップ - 1960〜70年代のコンピュータ・アート

まずは当時のプログラミング環境について確認しておきましょう。コンピュータを使える場所は大学や研究所が中心で、限られた一部のエンジニア、プログラマーのみが触れることができました。そのような時代のコンピュータ・アートは、どのようなものだったのでしょうか?

### Spacewar!

最初期のコンピュータゲーム “Spacewar!” (1962) です。

- 動画: [https://youtu.be/1EWQYAfuMYw?t=893](https://youtu.be/1EWQYAfuMYw?t=893)

![Spacewar!](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide51.jpg)

ブラウザで実際にプレイすることも可能です!

- [https://www.masswerk.at/spacewar/](https://www.masswerk.at/spacewar/)

![Spacewar! のエミュレーター](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide52.png)

### Herbert Franke

![Herbert Franke](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide53.png)

Herbert Franke は1927年、ウィーン生まれ。1950年代から、アナログコンピュータとオシロスコープによる作品を制作した、コンピュータアートのパイオニアです。

**Electronic Graphics, 1961-62** : アナログコンピュータとオシロスコープによる作品

![Herbert Franke, Electronic Graphics](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide54.jpg)

![Herbert Franke, Electronic Graphics](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide55.png)

![Herbert Franke, Electronic Graphics](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide56.png)

Herbert Franke のアナログ装置

![Herbert Franke のアナログ装置](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide57.png)

### Georg Nees

![Georg Nees](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide58.png)

Georg Nees は1926年、ニュルンベルク生まれ。1951年からシーメンス社に在籍し、デジタルコンピュータをプログラミングして図形生成を行ったパイオニアです。

**Georg Nees, 1965-1968.**

![Georg Nees の作品](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide59.png)

**Schotter, 1968.** : 作品とそのプログラム

![Georg Nees, Schotter](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide60a.jpg)

![Georg Nees, Schotter のプログラム](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide60b.png)

**'Plastik 1', 1965-8** : アルミレリーフ。工作機械をプログラムで制御して制作しています。

![Georg Nees, Plastik 1](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide61.png)

Georg Nees が使用していたプロッタ ZUSE Z64

![ZUSE Z64](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide62.jpg)

Georg Nees が使用していた頃のコンピュータ Siemens 2002

![Siemens 2002](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide63.png)

### A. Michael Noll

![A. Michael Noll](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide64.png)

A. Michael Noll は1939年生まれ。1961年から15年間、AT&Tベル研究所で基礎研究にとりくみました。

**“Vertical-Horizontal No. 3”, 1964 / “Gaussian Quadratic”, 1963**

![A. Michael Noll, Vertical-Horizontal No. 3](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide65a.png)

![A. Michael Noll, Gaussian Quadratic](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide65b.png)

**“Ninety Parallel Sinusoids With Linearly Increasing Period”, 1964**

![A. Michael Noll, Ninety Parallel Sinusoids With Linearly Increasing Period](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide66.png)

**“Four computer-generated random patterns”, 1965**

![A. Michael Noll, Four computer-generated random patterns](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide67.png)

この作品は、モンドリアンの「線によるコンポジション (1917)」をベースにしています。

![モンドリアン「線によるコンポジション」](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide68.png)

### Frieder Nake

![Frieder Nake](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide69.png)

Frieder Nake は1938年、ドイツ、シュトゥットガルト生まれ。

**13/9/65 Nr. 2, 1965**

![Frieder Nake, 13/9/65 Nr. 2](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide70.jpg)

**Frieder Nake, 1965**

![Frieder Nake, 1965](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide71.png)

### Manfred Mohr

![Manfred Mohr](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide72.png)

Manfred Mohr は1938年ドイツ生まれ。1963年からパリ、1981年からニューヨークに在住して制作しています。

**"a formal language", 1970**

![Manfred Mohr, a formal language](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide73.jpg)

**“Cubic Limit”, 1972-77**

![Manfred Mohr, Cubic Limit](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide74.png)

### Computer Technique Group (CTG)

![Computer Technique Group](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide75.png)

Computer Technique Group (CTG) は、槌屋治紀と幸村真佐男の出会いをきっかけに、1966年12月に山中邦夫と柿崎純一郎を加えた４人（最終的に10名）で結成されたコンピュータ・アート集団です。

**Running Cola is Africa, 1969**

![Computer Technique Group, Running Cola is Africa](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide76.jpg)

**Shot Kennedy, 1967**

![Computer Technique Group, Shot Kennedy](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide77.png)

### 現代のコードによる表現

現代でも、コードによる美学の探求は進められています。例えば [Casey Reas](http://reas.com/) の Process Compendium 2004-2010 です。

- [https://vimeo.com/22955812](https://vimeo.com/22955812)

![Casey Reas, Process Compendium](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide78a.png)

![Casey Reas, Process Compendium](https://raw.githubusercontent.com/tado/sfc-design/main/img/02_slide78b.png)

現在では、PCさえあれば誰でもコードによる表現ができる時代です。先人たちの作品も参考にしながら、コードによる「かたち」の表現を探求していきましょう!
