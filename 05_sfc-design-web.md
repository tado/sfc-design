---
title: "p5.jsで画像データを扱う – 画像の分析・再合成"
date: 2026-10-26T11:10:50+09:00
url: "/sfc-design26/05_sfc-design-web.html"
categories: ["sfc-design26"]
summary: "今回は、p5.jsで画像ファイルを読み込み、そのデータを分析して、新たなイメージとして再合成する方法について学びます。 まず始めに、ビットマップ画像がどのようなしくみで表示されているのか、ピクセルとRGBAのデータ構造から解説します。 次に、p5.Imageを使って画像を表示し、tint() で色や透明度を変更します。さらに、img.get() で画像のピクセルの色を取り出し、…"
image: "https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide30.jpg"
---

![円の大きさと色で画像を再構成する](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide30.jpg?ssl=1)

今回は、p5.jsで画像ファイルを読み込み、そのデータを分析して、新たなイメージとして再合成する方法について学びます。

まず始めに、ビットマップ画像がどのようなしくみで表示されているのか、ピクセルとRGBAのデータ構造から解説します。

次に、p5.Imageを使って画像を表示し、tint() で色や透明度を変更します。さらに、img.get() で画像のピクセルの色を取り出し、その色や明度、彩度をもとに円や四角形で画像を再構成 (ピクセレイト) してみます。

最後に、マウスの位置を使ったインタラクティブな工夫として、画像のモザイク化とスキャンに挑戦してみましょう。

## 本日の課題

テーマ: 「画像データで表現する」

p5.jsに読み込んだ画像ファイルのデータで表現してみましょう! p5.Imageに読み込んだ画像ファイルの情報から、新たなイメージを生成します。同じ写真でも、色を取り出す場所や、どんな図形で描き直すか、明度や彩度を何に対応させるかによって、まったく違った表現になります。読み込む画像は自由です。次回の授業の冒頭で簡単に作品をいくつか紹介します。

提出方法は以下の通りです。

- 完成した作品には、(かっこいい) タイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出
- 必ず TAGS: [sfc261030](https://openprocessing.org/browse?q=sfc261030&time=anytime&type=tags&offset=0) を入れてください
- 前回の[提出作品](https://openprocessing.org/browse?q=sfc261023&time=anytime&type=tags&offset=0)で良いと思った作品を1つ選んでください
- 提出期限 11/5/2026

[課題提出フォーム](https://docs.google.com/forms/d/e/1FAIpQLSdrf_q_BhOVFu71nG6MCat8_uuRo5TWkCp2JAow6ASTmvEKZg/viewform?usp=publish-editor)

## スライド資料

[スライド資料: p5.jsで画像データを扱う – 画像の分析・再合成](https://drive.google.com/file/d/1qrmJLm_T8B9lbxpVwMPxbCh4QWF79AD8/view?usp=sharing)

## 今日の内容

- ビットマップ画像のしくみ
- 画像を表示する (p5.Image)
- 画像の色や透明度を変更する (tint)
- 画像をピクセレイト (img.get)
- 応用: インタラクティブな工夫 (モザイク化、スキャン)
- 実習

## ビットマップ画像のしくみ

### ピクセル

そもそも、コンピュータのモニタには、どのようなしくみで画像が映しだされているのでしょうか? 画像は、グリッド状に並んだ「ピクセル」という点の集合で構成されています。巨大なエクセルの表のようなイメージです。

![画像を拡大するとピクセルが見える](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide03a.png?ssl=1)

![拡大した目のピクセル](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide03b.jpg?ssl=1)

例えば、640 x 480 pixel の画像データの場合、640 x 480 = 307,200 個のピクセルから構成された平面になります。

![640 x 480 pixelの画像](https://raw.githubusercontent.com/tado/sfc-design/main/img/05_slide04.svg)

様々な種類のモニタを拡大すると、ピクセルが見えます。

![様々な種類のモニタを拡大した様子](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide05.png?ssl=1)

### RGBAのデータ

それぞれのピクセルには、RGB (赤、緑、青) とアルファチャンネル A (透明度) のデータが格納されています (フルカラーの場合)。それぞれのチャンネルは、8bit = 256 の階調を持ちます。

![RGBAのチャンネル](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide06.png?ssl=1)

コンピュータの内部では、画像データは「ラスターイメージ」として扱われています。ラスターイメージとは、ビットマップ画像を、点が線上に並んだもの (ラスター) の集まりとして扱う方法です。

![ラスターイメージ](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide07.png?ssl=1)

1ピクセルの中では、画像の色数に応じてそれぞれの画素が順番に並んでいます。1画素あたり 8bit (0 〜 255) の値です。

![1ピクセルの中の画素の並び](https://raw.githubusercontent.com/tado/sfc-design/main/img/05_slide08.svg)

## 画像を表示する

### p5.Image と image()

p5.jsで画像を表示するには、p5.Imageクラスを使用します。Jpeg、GIF、PNG形式に対応しています。画像を表示するには、image() 関数を用います。

- image(画像ファイル名, x, y); – 座標(x, y)を左上にして、画像を表示
- image(画像ファイル名, x, y, width, height); – 座標(x, y)を左上にして、幅(width)と高さ(height)を指定して画像を表示

### 画像を配置する

p5.jsで画像を表示するためには、まず画像を配置 (またはアップロード) する必要があります。方法は2つあります。

- VSCodeなどのテキストエディターでローカルに使用する場合 : 画像を適切な場所にローカルに配置
- OpenProcessingの場合 : 画像をサーバーにアップロード

VSCodeなどで開発する場合は、例えばシンプルに全て同じフォルダに入れます (html, js, 画像)。

![同じフォルダに画像を配置](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide12.png?ssl=1)

OpenProcessingの場合は、まずSketchを保存した後、コードビューで右側のメニューを表示して、Filesタブを選択します。Upload Filesボタンを押して画像を選択 (またはドラッグ&ドロップ) すると、画像がアップロードされます。

![OpenProcessingで画像をアップロード](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide13.png?ssl=1)

### 画像を読み込む (async と await)

画像ファイルの読み込みには、loadImage() を使います。p5.js 2.0 以降では、async と await を使って画像を読み込みます。

- setup() の前に *async* をつけると、処理の完了を「待つ」ことができる関数になります
- loadImage() の前に *await* をつけると、画像の読み込みが終わるまで待ってから、次の行に進みます

画像ファイルの読み込みには少し時間がかかります。await をつけずに読み込むと、まだ読み込みが終わっていない画像を表示しようとしてしまいます。await で読み込みの完了を待つことで、次の行からは確実に画像を使うことができます。また、setup() が終わってから draw() が始まるので、draw() の中でも読み込んだ画像を使うことができます。

```javascript
async function setup() {
  createCanvas(windowWidth, windowHeight);
  img = await loadImage('./photo.jpg');
}
```

### 画像を表示するプログラム

画像を表示するプログラムは以下のようになります。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //左上を起点にして画像を表示
  image(img, 0, 0);
}
```

画像がオリジナルのサイズで表示されます。

![画像を表示 (オリジナルのサイズ)](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide16.jpg?ssl=1)

### 位置とサイズを指定する

次に、画像のサイズを画面の大きさにリサイズしてから表示してみましょう。img.resize() で画像をキャンバスのサイズに合わせます。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をキャンバスのサイズに合わせてリサイズ
  img.resize(width, height);
  //左上を起点にして画像を表示
  image(img, 0, 0);
}
```

画像が画面いっぱいに拡大して表示されます。

![画像を表示 (拡大)](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide18.jpg?ssl=1)

## 画像の色や透明度を変更する

### tint()

tint() 関数を使うと、image() で表示した画像の色や透明度を操作することができます。

- tint(gray) – 画像のレベルを変更
- tint(gray, alpha) – 画像のレベルと透明度を変更
- tint(red, green, blue) – RGBの値を変更
- tint(red, green, blue, alpha) – RGBの値と透明度を変更

### マウスY座標で明度を変化させる

イメージのレベルを、マウスのY座標で変化させてみましょう。mouseY を画面の高さで割って 0〜1 の値にし、255 をかけることで、マウスを下に動かすほど画像が明るくなります。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をキャンバスのサイズに合わせてリサイズ
  img.resize(width, height);
}

function draw() {
  background(0);
  //画像の明度をマウスのY座標で変更
  tint(mouseY / float(height) * 255);
  //色を変更した画像を表示
  image(img, 0, 0);
}
```

![イメージのレベルを変更](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide21.jpg?ssl=1)

### マウスの位置で色を変化させる

同じように、マウスの位置で画像の色 (RGBの値) を変化させてみます。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をキャンバスのサイズに合わせてリサイズ
  img.resize(width, height);
}

function draw() {
  background(0);
  //画像のRGB値をマウスの位置で変更
  let r = mouseX / float(width) * 255;
  let g = mouseY / float(height) * 255;
  let b = 255 - mouseX / float(width) * 255;
  tint(r, g, b);
  //色を変更した画像を表示
  image(img, 0, 0, width, height);
}
```

![イメージの色を変更](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide23.jpg?ssl=1)

## 画像をピクセレイト

### img.get()

いよいよ、画像のピクセルの情報にアクセスしてみましょう! img.get(x, y) を使うと、画像 img の (x, y) の位置にあるピクセルの色の情報を取得できます。これを使えば、画像の全てのピクセルの色を取り出すことができます。

### 画像の色で円を描く

ランダムな位置の色を画像から取得して、同じ場所に円を描画してみます。draw() が実行されるたびに円が1つずつ増えていき、だんだんと元の画像が浮かびあがってきます。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をキャンバスのサイズに合わせてリサイズ
  img.resize(width, height);
  //背景を黒に
  background(0);
}

function draw() {
  //色を取得する位置をランダムに決定
  let x = int(random(width));
  let y = int(random(height));
  //指定した場所の色を取得
  let col = img.get(x, y);
  fill(col, 127);
  noStroke();
  let diameter = 20;
  //円を描画
  circle(x, y, diameter);
}
```

![画像の色をピックアップして同じ場所に円を描画](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide27.jpg?ssl=1)

### 明度を円の大きさに反映させる

画像のピクセルの色情報をもとに、画像を再描画することを「ピクセレイト」と呼びます。円の大きさと色で、画像を再構成してみましょう。

- 色 : 円を描いた座標の、元画像での RGB の値
- 直径 : 元画像の座標での、色の明度

色の明度を求めるには、brightness(色) を使います。求めた明度を map() で円の直径に変換します。また、draw() の中で for文を使って一度に10個の円を描くことで、描画をスピードアップしています。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をリサイズ
  img.resize(width, height);
  background(0);
}

function draw() {
  //10倍速で描画
  for (let i = 0; i < 10; i++) {
    //色を取得する位置をランダムに決定
    let x = int(random(width));
    let y = int(random(height));
    //指定した場所の色を取得
    let col = img.get(x, y);
    fill(red(col), green(col), blue(col), 127);
    noStroke();
    //色の明度を円の直径に反映させる
    let diameter = map(brightness(col), 0, 255, 1, 80);
    //円を描画
    circle(x, y, diameter);
  }
}
```

明度がサイズに対応して、明るいところほど大きな円で描かれます。

![明度がサイズに対応](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide30.jpg?ssl=1)

### 彩度を円の大きさに反映させる

今度は、色の明度ではなく、彩度を円のサイズに対応させてみましょう。彩度が高いポイントは大きな円で描かれ、また違った効果が生まれます。彩度を求めるには、saturation(色) を使います。

色に透明度を加えるには、red()、green()、blue() でRGBの値を個別に取り出し、そこに透明度を付加します。

```javascript
fill(red(col), green(col), blue(col), 127);
```

さらに、blendMode(ADD) で混色を加算合成にしています。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をリサイズ
  img.resize(width, height);
  //混色を加算合成に
  blendMode(ADD);
  //背景を黒に
  background(0);
}

function draw() {
  //一度に10個の円を生成
  for (let i = 0; i < 10; i++) {
    //色を取得する位置をランダムに決定
    let x = int(random(width));
    let y = int(random(height));
    //指定した場所の色を取得
    let col = img.get(x, y);
    fill(red(col), green(col), blue(col), 190);
    noStroke();
    //色の彩度を円の直径にする
    let diameter = map(saturation(col), 0, 255, 1, 40);
    //円を描画
    circle(x, y, diameter);
  }
}
```

![彩度がサイズに対応](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide33.jpg?ssl=1)

### 四角形の長さと角度で再構成する

円ではなく、四角形の長さと回転角度で再合成してみましょう。

- 四角形の長さ : 明度に対応させる
- 四角形の角度 : 彩度に対応させる

push() と pop() で座標系を保存・復元しながら、translate() で描画する位置に原点を移動し、rotate() で回転させてから細長い四角形を描きます。一度に100個の四角形を描いています。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像をリサイズ
  img.resize(width, height);
  //背景を黒に
  background(0);
}

function draw() {
  for (let i = 0; i < 100; i++) { //100倍速
    //色を取得する位置をランダムに決定
    let x = int(random(width));
    let y = int(random(height));
    //指定した場所の色を取得
    let col = img.get(x, y);
    noStroke();
    //彩度を回転角度に反映させる
    let rotation = map(saturation(col), 0, 255, 0, 360);
    //長さは明度に反映させる
    let length = map(brightness(col), 0, 255, 0, 100);
    //色に透明度を加える
    fill(red(col), green(col), blue(col), 128);
    push();
    translate(x, y);
    rotate(radians(rotation));
    //四角形を描画
    rect(0, 0, 2, length);
    pop();
  }
}
```

![四角形の大きさと角度で画像を再構成](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide36.jpg?ssl=1)

## 応用: インタラクティブな工夫

### 画像をモザイク化する

マウスの位置によって、インタラクションしてみましょう。マウスの位置は、mouseX (マウスのx座標) と mouseY (マウスのy座標) で取得できます。

マウスの位置でモザイクの大きさが変化するプログラムです。画面の幅と高さで二重のfor文をまわし、一定の間隔で取得した色で四角形を描くことで、モザイク状の画像になります。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像を画面の大きさにリサイズ
  img.resize(width, height);
  //背景を黒に
  background(0);
}

function draw() {
  background(0);
  noStroke();
  //モザイクの粒度をマウスの座標で決定
  let stepX = mouseX / 10.0;
  let stepY = mouseY / 10.0;
  //モザイクの最小値を20に
  if (stepX < 20) {
    stepX = 20;
  }
  if (stepY < 20) {
    stepY = 20;
  }
  //画面の幅と高さでループ
  for (let j = 0; j < height; j = j + stepY) {
    for (let i = 0; i < width; i = i + stepX) {
      //座標を指定して色を取得
      let c = img.get(i, j);
      //取得した色を塗りの色に
      fill(c);
      //四角形を描画
      rect(i, j, stepX, stepY);
    }
  }
}
```

![マウスの位置でモザイクの大きさが変化](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide40.jpg?ssl=1)

### 画像ファイルをスキャンする

img.get() を活用して、画像の特定のy座標の色だけをとりだし、バーコード状に並べてみましょう。写真をスキャナーでスキャンしているイメージです。マウスの位置でスキャンする高さを変更します。

```javascript
let img; //画像データ

async function setup() {
  createCanvas(windowWidth, windowHeight);
  //画像をロード (読み込みが終わるまで待つ)
  img = await loadImage('./photo.jpg');
  //画像を画面の大きさにリサイズ
  img.resize(width, height);
  //背景を黒に
  background(0);
}

function draw() {
  background(0);
  noStroke();
  //画面の幅だけループ
  for (let i = 0; i < width; i++) {
    //現在のマウスのY座標の色を取得
    let c = img.get(i, mouseY);
    //取得した色を塗りの色に
    fill(c);
    //画面の高さいっぱいに幅1pixの長方形を描画
    rect(i, 0, 1, height);
  }
}
```

![マウスの位置でスキャンする高さを変更](https://i0.wp.com/raw.githubusercontent.com/tado/sfc-design/main/img/05_slide43.jpg?ssl=1)

## 関連リンク

- [p5.js Web Editor](https://editor.p5js.org/)
- [p5.js リファレンス](https://p5js.org/reference/)
- [p5.js リファレンス: async / await](https://p5js.org/reference/p5/async_await/)
- [p5.js リファレンス: loadImage()](https://p5js.org/reference/p5/loadImage/)
- [p5.js リファレンス: image()](https://p5js.org/reference/p5/image/)
- [p5.js リファレンス: p5.Image](https://p5js.org/reference/p5/p5.Image/)
- [p5.js リファレンス: tint()](https://p5js.org/reference/p5/tint/)
- [p5.js リファレンス: brightness()](https://p5js.org/reference/p5/brightness/)
- [p5.js リファレンス: saturation()](https://p5js.org/reference/p5/saturation/)
- [p5.js リファレンス: map()](https://p5js.org/reference/p5/map/)
- [p5.js リファレンス: blendMode()](https://p5js.org/reference/p5/blendMode/)
- [p5.js リファレンス: mouseX](https://p5js.org/reference/p5/mouseX/)
- [OpenProcessing](https://www.openprocessing.org/)

## 本日の課題

テーマ: 「画像データで表現する」

p5.jsに読み込んだ画像ファイルのデータで表現してみましょう! p5.Imageに読み込んだ画像ファイルの情報から、新たなイメージを生成します。同じ写真でも、色を取り出す場所や、どんな図形で描き直すか、明度や彩度を何に対応させるかによって、まったく違った表現になります。読み込む画像は自由です。次回の授業の冒頭で簡単に作品をいくつか紹介します。

提出方法は以下の通りです。

- 完成した作品には、(かっこいい) タイトルをつける
- 完成した作品はOpenProcessingに投稿してURLを提出
- 必ず TAGS: [sfc261030](https://openprocessing.org/browse?q=sfc261030&time=anytime&type=tags&offset=0) を入れてください
- 前回の[提出作品](https://openprocessing.org/browse?q=sfc261023&time=anytime&type=tags&offset=0)で良いと思った作品を1つ選んでください
- 提出期限 11/5/2026

[課題提出フォーム](https://docs.google.com/forms/d/e/1FAIpQLSdrf_q_BhOVFu71nG6MCat8_uuRo5TWkCp2JAow6ASTmvEKZg/viewform?usp=publish-editor)
