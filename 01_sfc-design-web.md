# オリエンテーション

![p5.jsとGitHub Copilotによるコード生成のデモ](./img/01_slide12.png)

「デザインとプログラミング」初回は、まずこの講義の概要と進め方について説明していきます。

続いて、生成AIとの付き合い方について考えます。慶應義塾や他大学のガイドラインを参照しながら、この講義で生成AIをどのように扱っていくのかを説明します。

その後は「なぜプログラミングが必要なのか?」という問いに対する回答として「ハイブリッドを目指そう」というテーマでプログラマーの歴史について解説します。

最後に次回までの課題について説明して本日は終了です。

## スライド資料

<!-- スライド資料へのリンクを追加 -->

## 講義の進めかた

この講義では K-LMS (SFC SOL) はあまり活用しません。その代わりに、講義資料はこのページ [デザインとプログラミング2026](https://yoppa.org/sfc-design26) に掲載していきます。

理想の講義構成は以下のとおりです (初回の今日は例外です)。

- 講義前半
  - 前回の提出課題の講評
  - 提出された課題をベースにしたコードの応用例など
  - 参考になる作品などの紹介
- 講義後半
  - 次回までの課題出題
  - 課題を作成するための教材の提示

## 生成AIについて

生成AI (Generative AI) は、とてつもないスピードで進化しています。文章・画像・動画・音声、そしてプログラムまで生成できるようになり、さらに質問に答えるだけでなく、自律的にコードを書いて実行・修正まで行う「AIエージェント」へと進化しつつあります。この講義では生成AIをどう扱っていくのか、一緒に考えていきましょう。

### 主な生成AIサービス

- 生成AI提供企業: Google ([Gemini](https://gemini.google.com/))、OpenAI ([ChatGPT](https://chatgpt.com/))、Anthropic ([Claude](https://claude.ai/))、Microsoft ([Copilot](https://copilot.microsoft.com/))、xAI ([Grok](https://grok.com/)) など
- コード生成AI: [Gemini (Antigravity)](https://antigravity.google/)、[Codex](https://openai.com/codex/)、[Claude (Claude Code)](https://claude.com/product/claude-code)、[GitHub Copilot](https://github.com/features/copilot)、[Cursor](https://cursor.com/) など
- 画像・動画生成AI: [Midjourney](https://www.midjourney.com/)、[Nano Banana](https://gemini.google/overview/image-generation/)、[Veo](https://deepmind.google/models/veo/)、[Adobe Firefly](https://firefly.adobe.com/) など

### 慶應義塾の生成AI利用ガイドライン

![慶應義塾における生成AIの利用ガイドライン](./img/01_keio-ai-guideline.png)

慶應義塾では「[慶應義塾における生成AIの利用ガイドライン](https://keio-univ.notion.site/ai-guideline)」が公開されています。基本姿勢は **「リスクを正しく理解しながら、生成AIを積極的に活用する」** というものです。この講義でもこの方針を支持します。禁止するのではなく、どう活用するかを考えて行動していくことが重要です。

ガイドラインでは、keio.jp アカウントでログインして使う「法人全体契約AI」を優先して使うよう求めています。法人全体契約AIでは、入力したデータがAIの学習に使われません (データ保護あり)。学生が使える法人全体契約AIは以下のとおりです (2026年7月時点)。

- **Google Gemini / Gemini Notebook** (旧 NotebookLM) : 調査・要約・文章作成、手元の資料にもとづく質問応答
- **Microsoft 365 Copilot Chat** : エンタープライズデータ保護 (EDP) を適用

一方で、個人のアカウントや無料のAIサービスはデータ保護の対象外です。Google検索の「AIモード」や Google AI Studio も義塾のサービスの対象外となっています。

このほか、ガイドラインでは以下のような点に注意するよう求めています。

- 授業・レポート・課題での利用は、シラバスや担当教員の方針に従う
- 個人情報・機密情報は、法人全体契約AI以外には入力しない
- 出力は必ずファクトチェックする (ハルシネーションに注意)
- AIの生成物が、既存の著作物や他人の肖像などの権利を侵害していないか確認する
- 読み込ませた文書やWebページに紛れ込んだ指示による誘導に注意する
- **最終的な判断と責任は、使う本人にある**

### 京都産業大学の生成AI利用ガイドライン

![京都産業大学 生成AI利用ガイドライン](./img/01_kyoto-su-ai-guideline.png)

他大学の例として、「[京都産業大学 生成AI利用ガイドライン](https://www.kyoto-su.ac.jp/torikumi/ai-basic-stance/ai-guideline/)」(2026年7月) も紹介します。学生向けに「活用指針・遵守事項・リスク」を具体的な事例つきで解説していて、とても参考になります。生成AIは使い方と心がけ次第で、学びの支援にも妨げにもなるという考え方です。

- Ⅰ 学びのための活用指針
  - AIを思考の代替ではなく **支援ツール** として活用する
  - ファクトチェックを徹底する
  - アイデア出し、論点整理、プログラミングの補助など、学びの支援として活用する
- Ⅱ 学びの誠実性に関するルール
  - 【最優先】授業ごとの指示・条件を守る
  - AI生成物の無断提出 (丸写し / コピペ) の禁止
  - 課題丸投げ (思考過程丸投げ) の禁止
- Ⅲ 理解すべきリスク
  - バイアスを含んだ情報 / 情報漏洩と個人情報・機密情報 / 著作権侵害

特に印象的なのが **「認知的な借金」** という考え方です。課題の丸投げは、長期的には考える力を低下させる「認知的な借金」になるとしています。ガイドラインでは、以下のような利用例が挙げられています。

- 学びを損なう利用例
  - 課題を終わらせることだけを目的に、AIに短時間でやらせる
  - 提出物はよくできていても、質問されると自分の言葉で説明できない
  - 卒論のテーマや、自分が何に興味を持つべきかまでAIに決めてもらう
- 不正行為につながる利用例
  - AIが生成した文章をほとんど修正せずに提出する
  - AIが挙げた参考文献を、実在するか確認せずに記載する
  - 自分では説明できない内容を提出する

### この講義での生成AIの扱い

この講義では、生成AIを以下のように扱います (他の講義についてはその指示に従ってください)。

- 生成AIは基本的に使用しても良い
- ただ結果をそのままコピペするのではなく、より生産的な使用方法を考える
- 生成された結果が誤りである可能性を常に考慮する
  - ソースにあたる (Web検索機能を使うと、多くの生成AIで出典が表示される)
  - 生成AIと検索を併用する
  - ...など

いろいろ試行錯誤しながら一緒に考えていきましょう!

### Gemini 学割プラン

![Google Gemini 学割プラン](./img/01_gemini-students.png)

[Google Gemini 学割プラン](https://gemini.google/jp/students/?hl=ja) を利用すると、Google AI Plus が **1年間無料** になります。

- 18歳以上の大学生が対象、2026年12月31日までに登録
- Geminiの利用上限が2倍、400GBのストレージ、学習ノートブック、Gemini Live など
- 登録時に支払い方法の登録が必要 (解約しなければ無料期間後は毎月¥725)

ただし、これは個人のGoogleアカウントでの契約なので、keio.jp の Gemini (法人全体契約AI) とは別物です。慶應のガイドラインでは「個別契約AI」扱いとなるので、個人情報・機密情報は入力しないようにしてください。

### 参考: Text-GPT-p5

![Text-GPT-p5](./img/01_slide10.png)

[Text-GPT-p5](https://text-gpt-p5.vercel.app/) は、この講義で使用する p5.js のコードを GPT-4o-mini を用いて対話的に生成できるツールです。オープンソースで公開されています。

### 生成AIを使用したプログラミングのデモ

p5.js (この講義で使用する環境) と GitHub Copilot (コード生成) を組み合わせて、生成AIを使用したプログラミングのデモを行います。設定方法などはまた後日解説します!

## イントロダクション – ハイブリッドを目指そう!

### プログラマーの歴史 - ハッカーからハイブリッドへ

![History of the Future, Art & Technology from 1965 - Yesterday](./img/01_slide14.png)

History of the Future, Art & Technology from 1965 - Yesterday | Casey Reas | The Gray Area Festival

[https://youtu.be/mHox98NFU3o](https://youtu.be/mHox98NFU3o)

この講演の中で Casey Reas は、プログラミングの超略史を以下の4つの段階で紹介しています。

1. リアル・プログラマー
2. ハッカー
3. アマチュア
4. ハイブリッド

### “Real Programmer”

最初の段階は、リアル・プログラマー、つまり「ガチの」プログラマーの時代です。1940年代から50年代にかけての時代です。

![リアル・プログラマーの時代](./img/01_slide17.jpg)

コンピュータ黎明期のプログラマーは女性が多かったことも特徴です。

![コンピュータ黎明期の女性プログラマー](./img/01_slide18a.png)

![コンピュータ黎明期の女性プログラマー](./img/01_slide18b.jpg)

参考: [ENIAC Programmers Project](http://eniacprogrammers.org/)

![ENIAC Programmers Project](./img/01_slide19.jpg)

### Hackers

次はハッカーの時代です。1960年代から70年代にかけて、コンピュータは国家プロジェクトから大学・研究所へと広がっていきました。

![Ken Thompson and Dennis Ritchie at PDP-11](./img/01_slide21.jpg)

*Ken Thompson and Dennis Ritchie at PDP-11*

この時代には、PDP-11 などのミニコン (ミニコンピュータ) が普及しました。

![PDP-11](./img/01_slide22.jpg)

ハッカーの時代には、コンピュータ・ゲームも誕生しています。

- Spacewar! (MIT 1962) : [https://youtu.be/Rmvb4Hktv7U](https://youtu.be/Rmvb4Hktv7U)

![Spacewar!](./img/01_slide23.jpg)

ハッカーについて考える上で参考になるのが、Paul Graham によるエッセイ「[ハッカーと画家 - Hackers and Painters -](http://practical-scheme.net/trans/hp-j.html)」(May 2003) です。

![Hackers & Painters](./img/01_slide24.jpg)

> “ハッカーと画家に共通することは、どちらもものを創る人間だということだ。 作曲家や建築家や作家と同じように、ハッカーと画家がやろうとしているのは、 良いものを創るということだ。 良いものを創ろうとする過程で新しいテクニックを発見することがあり、 それはそれで良いことだが、いわゆる研究活動とはちょっと違う。”

### Amateurs

1980年代になると、ホビーとしてのパソコンが登場し、アマチュアの時代が始まります。

![ホビーとしてのパソコン](./img/01_slide26.jpg)

1980年代には、日本でも「マイコンブーム」が起こりました。

![FM-7の広告](./img/01_slide27a.jpg)

![PC-8801mkIISRの広告](./img/01_slide27b.jpg)

**Apple II (1977)** : Apple I の後継として、スティーブ・ウォズニアックが開発しました。世界初の個人向けに販売された、完成品マイクロコンピュータです。

![Apple II](./img/01_slide28.jpg)

**Commodore 64 (1982)** : 単一機種としては最も販売台数の多いパーソナルコンピュータです。販売台数は1250万から1700万台といわれています。

![Commodore 64](./img/01_slide29.jpg)

当時のパソコンでは、BASICを使って誰でも手軽にプログラミングを楽しむことができました。例えば、HELLO WORLDをひたすらくりかえすプログラムは、以下のたった2行で書けます。

```basic
10 print "hello world!!"
20 goto 10
```

![HELLO WORLDをくりかえす](./img/01_slide30.png)

ちょっと変更して、改行を削除してみます。

```basic
10 print "hello world!!";
20 goto 10
```

![改行を削除](./img/01_slide31.png)

次に、ランダムに文字を出力してみます。

```basic
10 print chr$(32+96*rnd(1));
```

![ランダムに文字を出力](./img/01_slide32.png)

出力する文字を2種類の斜線に限定すると、迷路のような模様が!!

```basic
10 print chr$(205.5+rnd(1));
```

![迷路のような模様](./img/01_slide33.png)

数値を変えると、いろいろなバリエーションを作ることができます。

```basic
10 print chr$(205.1+rnd(1));
10 print chr$(205.9+rnd(1));
10 print chr$(198.5+rnd(1));
10 print chr$(204+(int(rnd(1)+.5)*3));
10 print chr$(204+(rnd(1)+.5)*3);
10 print chr$(181+(int(rnd(1)+.5)*3)+(ing(rnd(1)+.5)));
10 print chr$(181+(int(rnd(1)+.5)*3));
10 poke 1024+rnd(1)*1000,77.5+rnd(1)
```

参考: 10 PRINT [http://10print.org/](http://10print.org/)

![10 PRINT](./img/01_slide35.png)

### Hybrids

リアル・プログラマー → ハッカー → アマチュアと来て、次に来るものは何でしょうか? それは、ハイブリッドなプログラマーです。では、ハイブリッド (Hybrid) の意味するものとは何でしょう?

![‘the carrier’ by patricia piccinini, 2012](./img/01_slide37.jpg)

*‘the carrier’ by patricia piccinini, 2012*

これからは、専業プログラマーの時代ではありません。他に専門をもったプログラマーの時代です。

- アート
- デザイン
- 建築
- 広告
- 統計
- 政治
- 経済
- ...etc

プログラマー以外の専門家もプログラミングをする時代です。両方の知識と技術をハイブリッドしていきましょう。

**ハイブリッドを目指しましょう!**

## 関連リンク

- [慶應義塾における生成AIの利用ガイドライン](https://keio-univ.notion.site/ai-guideline)
- [京都産業大学 生成AI利用ガイドライン](https://www.kyoto-su.ac.jp/torikumi/ai-basic-stance/ai-guideline/)
- [Google Gemini 学割プラン](https://gemini.google/jp/students/?hl=ja)
- [Text-GPT-p5](https://text-gpt-p5.vercel.app/)
- [GitHub Copilot](https://github.com/features/copilot)
- [GitHub Copilot in VS Code](https://code.visualstudio.com/docs/copilot/overview)
- [学生としてGitHub Educationに応募する](https://docs.github.com/ja/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-education-for-students/apply-to-github-education-as-a-student)

## 次回までの課題

1\. まず今後の講義で使用する開発環境を準備していきます。

- 最新の[Google Chrome](https://www.google.com/chrome/)をインストール
- [Visual Studio Code](https://code.visualstudio.com/)をインストール (環境設定は次回やります)

2\. 作品を共有するためのプラットフォームに加入します。

- [OpenProcessing](https://openprocessing.org/)にユーザー登録

3\. 最後に以下のオンラインフォームに回答してください。

- [https://forms.gle/Hjf85SkGLy5eGAEs6](https://forms.gle/Hjf85SkGLy5eGAEs6)

以上3点です! 締切は次回の授業の前日までとします!
