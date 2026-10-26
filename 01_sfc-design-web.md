---
title: "オリエンテーション"
date: "2026-09-27T10:08:05+09:00"
lastmod: "2026-09-27T12:38:08+09:00"
url: "/sfc-design26/19679.html"
categories: ["sfc-design26"]
summary: "「デザインとプログラミング」初回は、まずこの講義の概要と進め方について説明していきます。続いて、生成AIとの付き合い方について考えます。慶應義塾や他大学のガイドラインを参照しながら、この講義で生成AIをどのように扱っていくのかを説明します。その後は「なぜプログラミングが必要なのか?」という問いに対する回答として「ハイブリッドを目指そう」というテーマでプログラマーの歴史について解説します。最後に次回…"
wp_id: 19679
shortlink: "https://wp.me/pU1U9-57p"
---

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1920" height="1149" src="/wp-content/uploads/2026/09/01_slide12.png" alt="p5.jsとGitHub Copilotによるコード生成のデモ" class="wp-image-19692" srcset="/wp-content/uploads/2026/09/01_slide12-300x180.png 300w, /wp-content/uploads/2026/09/01_slide12-768x460.png 768w, /wp-content/uploads/2026/09/01_slide12-1024x613.png 1024w, /wp-content/uploads/2026/09/01_slide12-1536x919.png 1536w, /wp-content/uploads/2026/09/01_slide12.png 1920w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

「デザインとプログラミング」初回は、まずこの講義の概要と進め方について説明していきます。

続いて、生成AIとの付き合い方について考えます。慶應義塾や他大学のガイドラインを参照しながら、この講義で生成AIをどのように扱っていくのかを説明します。

その後は「なぜプログラミングが必要なのか?」という問いに対する回答として「ハイブリッドを目指そう」というテーマでプログラマーの歴史について解説します。

最後に次回までの課題について説明して本日は終了です。

## スライド資料

- [スライド資料 (PDF)](https://drive.google.com/file/d/1Qb5c_erxIrXLp4pW_dlVV1R51NwZZbQK/view?usp=sharing)

## 講義の進めかた

この講義では K-LMS (SFC SOL) はあまり活用しません。その代わりに、講義資料はこのページ[デザインとプログラミング2026](/sfc-design26)に掲載していきます。

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
- コード生成AI:[Gemini (Antigravity)](https://antigravity.google/)、[Codex](https://openai.com/codex/)、[Claude (Claude Code)](https://claude.com/product/claude-code)、[GitHub Copilot](https://github.com/features/copilot)、[Cursor](https://cursor.com/)など
- 画像・動画生成AI:[Midjourney](https://www.midjourney.com/)、[Nano Banana](https://gemini.google/overview/image-generation/)、[Veo](https://deepmind.google/models/veo/)、[Adobe Firefly](https://firefly.adobe.com/)など

### 慶應義塾の生成AI利用ガイドライン

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1320" height="720" src="/wp-content/uploads/2026/09/01_keio-ai-guideline.png" alt="慶應義塾における生成AIの利用ガイドライン" class="wp-image-19682" srcset="/wp-content/uploads/2026/09/01_keio-ai-guideline-300x164.png 300w, /wp-content/uploads/2026/09/01_keio-ai-guideline-768x419.png 768w, /wp-content/uploads/2026/09/01_keio-ai-guideline-1024x559.png 1024w, /wp-content/uploads/2026/09/01_keio-ai-guideline.png 1320w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

慶應義塾では「[慶應義塾における生成AIの利用ガイドライン](https://keio-univ.notion.site/ai-guideline)」が公開されています。基本姿勢は<strong>「リスクを正しく理解しながら、生成AIを積極的に活用する」</strong>というものです。この講義でもこの方針を支持します。禁止するのではなく、どう活用するかを考えて行動していくことが重要です。

ガイドラインでは、keio.jp アカウントでログインして使う「法人全体契約AI」を優先して使うよう求めています。法人全体契約AIでは、入力したデータがAIの学習に使われません (データ保護あり)。学生が使える法人全体契約AIは以下のとおりです (2026年7月時点)。

- **Google Gemini / Gemini Notebook**(旧 NotebookLM) : 調査・要約・文章作成、手元の資料にもとづく質問応答
- **Microsoft 365 Copilot Chat**: エンタープライズデータ保護 (EDP) を適用

一方で、個人のアカウントや無料のAIサービスはデータ保護の対象外です。Google検索の「AIモード」や Google AI Studio も義塾のサービスの対象外となっています。

このほか、ガイドラインでは以下のような点に注意するよう求めています。

- 授業・レポート・課題での利用は、シラバスや担当教員の方針に従う
- 個人情報・機密情報は、法人全体契約AI以外には入力しない
- 出力は必ずファクトチェックする (ハルシネーションに注意)
- AIの生成物が、既存の著作物や他人の肖像などの権利を侵害していないか確認する
- 読み込ませた文書やWebページに紛れ込んだ指示による誘導に注意する
- **最終的な判断と責任は、使う本人にある**

### 京都産業大学の生成AI利用ガイドライン

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1300" height="600" src="/wp-content/uploads/2026/09/01_kyoto-su-ai-guideline.png" alt="京都産業大学 生成AI利用ガイドライン" class="wp-image-19687" srcset="/wp-content/uploads/2026/09/01_kyoto-su-ai-guideline-300x138.png 300w, /wp-content/uploads/2026/09/01_kyoto-su-ai-guideline-768x354.png 768w, /wp-content/uploads/2026/09/01_kyoto-su-ai-guideline-1024x473.png 1024w, /wp-content/uploads/2026/09/01_kyoto-su-ai-guideline.png 1300w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

他大学の例として、「[京都産業大学 生成AI利用ガイドライン](https://www.kyoto-su.ac.jp/torikumi/ai-basic-stance/ai-guideline/)」(2026年7月) も紹介します。学生向けに「活用指針・遵守事項・リスク」を具体的な事例つきで解説していて、とても参考になります。生成AIは使い方と心がけ次第で、学びの支援にも妨げにもなるという考え方です。

- Ⅰ 学びのための活用指針
  - AIを思考の代替ではなく**支援ツール**として活用する
  - ファクトチェックを徹底する
  - アイデア出し、論点整理、プログラミングの補助など、学びの支援として活用する
- Ⅱ 学びの誠実性に関するルール
  - 【最優先】授業ごとの指示・条件を守る
  - AI生成物の無断提出 (丸写し / コピペ) の禁止
  - 課題丸投げ (思考過程丸投げ) の禁止
- Ⅲ 理解すべきリスク
  - バイアスを含んだ情報 / 情報漏洩と個人情報・機密情報 / 著作権侵害

特に印象的なのが<strong>「認知的な借金」</strong>という考え方です。課題の丸投げは、長期的には考える力を低下させる「認知的な借金」になるとしています。ガイドラインでは、以下のような利用例が挙げられています。

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
  - …など

いろいろ試行錯誤しながら一緒に考えていきましょう!

### Gemini 学割プラン

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1440" height="630" src="/wp-content/uploads/2026/09/01_gemini-students.png" alt="Google Gemini 学割プラン" class="wp-image-19686" srcset="/wp-content/uploads/2026/09/01_gemini-students-300x131.png 300w, /wp-content/uploads/2026/09/01_gemini-students-768x336.png 768w, /wp-content/uploads/2026/09/01_gemini-students-1024x448.png 1024w, /wp-content/uploads/2026/09/01_gemini-students.png 1440w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

[Google Gemini 学割プラン](https://gemini.google/jp/students/?hl=ja)を利用すると、Google AI Plus が**1年間無料**になります。

- 18歳以上の大学生が対象、2026年12月31日までに登録
- Geminiの利用上限が2倍、400GBのストレージ、学習ノートブック、Gemini Live など
- 登録時に支払い方法の登録が必要 (解約しなければ無料期間後は毎月¥725)

ただし、これは個人のGoogleアカウントでの契約なので、keio.jp の Gemini (法人全体契約AI) とは別物です。慶應のガイドラインでは「個別契約AI」扱いとなるので、個人情報・機密情報は入力しないようにしてください。

### 参考: Text-GPT-p5

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1649" height="935" src="/wp-content/uploads/2026/09/01_slide10.png" alt="Text-GPT-p5" class="wp-image-19695" srcset="/wp-content/uploads/2026/09/01_slide10-300x170.png 300w, /wp-content/uploads/2026/09/01_slide10-768x435.png 768w, /wp-content/uploads/2026/09/01_slide10-1024x581.png 1024w, /wp-content/uploads/2026/09/01_slide10-1536x871.png 1536w, /wp-content/uploads/2026/09/01_slide10.png 1649w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

[Text-GPT-p5](https://text-gpt-p5.vercel.app/)は、この講義で使用する p5.js のコードを GPT-4o-mini を用いて対話的に生成できるツールです。オープンソースで公開されています。

### 生成AIを使用したプログラミングのデモ

p5.js (この講義で使用する環境) と GitHub Copilot (コード生成) を組み合わせて、生成AIを使用したプログラミングのデモを行います。設定方法などはまた後日解説します!

## イントロダクション – ハイブリッドを目指そう!

### プログラマーの歴史 – ハッカーからハイブリッドへ

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1610" height="848" src="/wp-content/uploads/2026/09/01_slide14.png" alt="History of the Future, Art &#038; Technology from 1965 - Yesterday" class="wp-image-19688" srcset="/wp-content/uploads/2026/09/01_slide14-300x158.png 300w, /wp-content/uploads/2026/09/01_slide14-768x405.png 768w, /wp-content/uploads/2026/09/01_slide14-1024x539.png 1024w, /wp-content/uploads/2026/09/01_slide14-1536x809.png 1536w, /wp-content/uploads/2026/09/01_slide14.png 1610w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

History of the Future, Art & Technology from 1965 – Yesterday | Casey Reas | The Gray Area Festival

<figure class="wp-block-embed is-type-video is-provider-youtube wp-block-embed-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio"><div class="wp-block-embed__wrapper">
<span class="embed-youtube" style="text-align:center; display: block;"><iframe loading="lazy" class="youtube-player" width="640" height="360" src="https://www.youtube.com/embed/mHox98NFU3o?version=3&#038;rel=1&#038;showsearch=0&#038;showinfo=1&#038;iv_load_policy=1&#038;fs=1&#038;hl=en-US&#038;autohide=2&#038;wmode=transparent" allowfullscreen="true" style="border:0;" sandbox="allow-scripts allow-same-origin allow-popups allow-presentation allow-popups-to-escape-sandbox"></iframe></span>
</div></figure>

この講演の中で Casey Reas は、プログラミングの超略史を以下の4つの段階で紹介しています。

1. リアル・プログラマー
2. ハッカー
3. アマチュア
4. ハイブリッド

### “Real Programmer”

最初の段階は、リアル・プログラマー、つまり「ガチの」プログラマーの時代です。1940年代から50年代にかけての時代です。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1202" height="919" src="/wp-content/uploads/2026/09/01_slide17.jpg" alt="リアル・プログラマーの時代" class="wp-image-19698" srcset="/wp-content/uploads/2026/09/01_slide17-300x229.jpg 300w, /wp-content/uploads/2026/09/01_slide17-768x587.jpg 768w, /wp-content/uploads/2026/09/01_slide17-1024x783.jpg 1024w, /wp-content/uploads/2026/09/01_slide17.jpg 1202w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

コンピュータ黎明期のプログラマーは女性が多かったことも特徴です。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="989" height="784" src="/wp-content/uploads/2026/09/01_slide18a.png" alt="コンピュータ黎明期の女性プログラマー" class="wp-image-19690" srcset="/wp-content/uploads/2026/09/01_slide18a-300x238.png 300w, /wp-content/uploads/2026/09/01_slide18a-768x609.png 768w, /wp-content/uploads/2026/09/01_slide18a.png 989w" sizes="auto, (max-width: 989px) 100vw, 989px" /></figure>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="702" height="478" src="/wp-content/uploads/2026/09/01_slide18b.jpg" alt="コンピュータ黎明期の女性プログラマー" class="wp-image-19685" srcset="/wp-content/uploads/2026/09/01_slide18b-300x204.jpg 300w, /wp-content/uploads/2026/09/01_slide18b.jpg 702w" sizes="auto, (max-width: 702px) 100vw, 702px" /></figure>

参考:[ENIAC Programmers Project](http://eniacprogrammers.org/)

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="988" height="473" src="/wp-content/uploads/2026/09/01_slide19.jpg" alt="ENIAC Programmers Project" class="wp-image-19691" srcset="/wp-content/uploads/2026/09/01_slide19-300x144.jpg 300w, /wp-content/uploads/2026/09/01_slide19-768x368.jpg 768w, /wp-content/uploads/2026/09/01_slide19.jpg 988w" sizes="auto, (max-width: 988px) 100vw, 988px" /></figure>

### Hackers

次はハッカーの時代です。1960年代から70年代にかけて、コンピュータは国家プロジェクトから大学・研究所へと広がっていきました。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1116" height="894" src="/wp-content/uploads/2026/09/01_slide21.jpg" alt="Ken Thompson and Dennis Ritchie at PDP-11" class="wp-image-19697" srcset="/wp-content/uploads/2026/09/01_slide21-300x240.jpg 300w, /wp-content/uploads/2026/09/01_slide21-768x615.jpg 768w, /wp-content/uploads/2026/09/01_slide21-1024x820.jpg 1024w, /wp-content/uploads/2026/09/01_slide21.jpg 1116w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

*Ken Thompson and Dennis Ritchie at PDP-11*

この時代には、PDP-11 などのミニコン (ミニコンピュータ) が普及しました。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="600" src="/wp-content/uploads/2026/09/01_slide22.jpg" alt="PDP-11" class="wp-image-19683" srcset="/wp-content/uploads/2026/09/01_slide22-300x225.jpg 300w, /wp-content/uploads/2026/09/01_slide22-768x576.jpg 768w, /wp-content/uploads/2026/09/01_slide22.jpg 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

ハッカーの時代には、コンピュータ・ゲームも誕生しています。

- Spacewar! (MIT 1962) :[https\://youtu.be/Rmvb4Hktv7U](https://youtu.be/Rmvb4Hktv7U)

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="500" height="340" src="/wp-content/uploads/2026/09/01_slide23.jpg" alt="Spacewar!" class="wp-image-19693" srcset="/wp-content/uploads/2026/09/01_slide23-300x204.jpg 300w, /wp-content/uploads/2026/09/01_slide23.jpg 500w" sizes="auto, (max-width: 500px) 100vw, 500px" /></figure>

ハッカーについて考える上で参考になるのが、Paul Graham によるエッセイ「[ハッカーと画家 – Hackers and Painters –](http://practical-scheme.net/trans/hp-j.html)」(May 2003) です。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="564" height="846" src="/wp-content/uploads/2026/09/01_slide24.jpg" alt="Hackers &#038; Painters" class="wp-image-19689" srcset="/wp-content/uploads/2026/09/01_slide24-200x300.jpg 200w, /wp-content/uploads/2026/09/01_slide24.jpg 564w" sizes="auto, (max-width: 564px) 100vw, 564px" /></figure>

<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="wp-block-paragraph">“ハッカーと画家に共通することは、どちらもものを創る人間だということだ。 作曲家や建築家や作家と同じように、ハッカーと画家がやろうとしているのは、 良いものを創るということだ。 良いものを創ろうとする過程で新しいテクニックを発見することがあり、 それはそれで良いことだが、いわゆる研究活動とはちょっと違う。”</p>
</blockquote>

### Amateurs

1980年代になると、ホビーとしてのパソコンが登場し、アマチュアの時代が始まります。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1024" height="708" src="/wp-content/uploads/2026/09/01_slide26.jpg" alt="ホビーとしてのパソコン" class="wp-image-19704" srcset="/wp-content/uploads/2026/09/01_slide26-300x207.jpg 300w, /wp-content/uploads/2026/09/01_slide26-768x531.jpg 768w, /wp-content/uploads/2026/09/01_slide26.jpg 1024w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

1980年代には、日本でも「マイコンブーム」が起こりました。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="460" height="600" src="/wp-content/uploads/2026/09/01_slide27a.jpg" alt="FM-7の広告" class="wp-image-19681" srcset="/wp-content/uploads/2026/09/01_slide27a-230x300.jpg 230w, /wp-content/uploads/2026/09/01_slide27a.jpg 460w" sizes="auto, (max-width: 460px) 100vw, 460px" /></figure>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="480" height="685" src="/wp-content/uploads/2026/09/01_slide27b.jpg" alt="PC-8801mkIISRの広告" class="wp-image-19694" srcset="/wp-content/uploads/2026/09/01_slide27b-210x300.jpg 210w, /wp-content/uploads/2026/09/01_slide27b.jpg 480w" sizes="auto, (max-width: 480px) 100vw, 480px" /></figure>

**Apple II (1977)**: Apple I の後継として、スティーブ・ウォズニアックが開発しました。世界初の個人向けに販売された、完成品マイクロコンピュータです。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="550" height="374" src="/wp-content/uploads/2026/09/01_slide28.jpg" alt="Apple II" class="wp-image-19701" srcset="/wp-content/uploads/2026/09/01_slide28-300x204.jpg 300w, /wp-content/uploads/2026/09/01_slide28.jpg 550w" sizes="auto, (max-width: 550px) 100vw, 550px" /></figure>

**Commodore 64 (1982)**: 単一機種としては最も販売台数の多いパーソナルコンピュータです。販売台数は1250万から1700万台といわれています。

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="800" height="506" src="/wp-content/uploads/2026/09/01_slide29.jpg" alt="Commodore 64" class="wp-image-19703" srcset="/wp-content/uploads/2026/09/01_slide29-300x190.jpg 300w, /wp-content/uploads/2026/09/01_slide29-768x486.jpg 768w, /wp-content/uploads/2026/09/01_slide29.jpg 800w" sizes="auto, (max-width: 800px) 100vw, 800px" /></figure>

当時のパソコンでは、BASICを使って誰でも手軽にプログラミングを楽しむことができました。例えば、HELLO WORLDをひたすらくりかえすプログラムは、以下のたった2行で書けます。

<pre class="wp-block-code"><code class="">10 print "hello world!!"
20 goto 10
</code></pre>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="720" height="566" src="/wp-content/uploads/2026/09/01_slide30.png" alt="HELLO WORLDをくりかえす" class="wp-image-19680" srcset="/wp-content/uploads/2026/09/01_slide30-300x236.png 300w, /wp-content/uploads/2026/09/01_slide30.png 720w" sizes="auto, (max-width: 720px) 100vw, 720px" /></figure>

ちょっと変更して、改行を削除してみます。

<pre class="wp-block-code"><code class="">10 print "hello world!!";
20 goto 10
</code></pre>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="720" height="566" src="/wp-content/uploads/2026/09/01_slide31.png" alt="改行を削除" class="wp-image-19702" srcset="/wp-content/uploads/2026/09/01_slide31-300x236.png 300w, /wp-content/uploads/2026/09/01_slide31.png 720w" sizes="auto, (max-width: 720px) 100vw, 720px" /></figure>

次に、ランダムに文字を出力してみます。

<pre class="wp-block-code"><code class="">10 print chr$(32+96*rnd(1));
</code></pre>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="720" height="566" src="/wp-content/uploads/2026/09/01_slide32.png" alt="ランダムに文字を出力" class="wp-image-19700" srcset="/wp-content/uploads/2026/09/01_slide32-300x236.png 300w, /wp-content/uploads/2026/09/01_slide32.png 720w" sizes="auto, (max-width: 720px) 100vw, 720px" /></figure>

出力する文字を2種類の斜線に限定すると、迷路のような模様が!!

<pre class="wp-block-code"><code class="">10 print chr$(205.5+rnd(1));
</code></pre>

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="720" height="566" src="/wp-content/uploads/2026/09/01_slide33.png" alt="迷路のような模様" class="wp-image-19699" srcset="/wp-content/uploads/2026/09/01_slide33-300x236.png 300w, /wp-content/uploads/2026/09/01_slide33.png 720w" sizes="auto, (max-width: 720px) 100vw, 720px" /></figure>

数値を変えると、いろいろなバリエーションを作ることができます。

<pre class="wp-block-code"><code class="">10 print chr$(205.1+rnd(1));
10 print chr$(205.9+rnd(1));
10 print chr$(198.5+rnd(1));
10 print chr$(204+(int(rnd(1)+.5)*3));
10 print chr$(204+(rnd(1)+.5)*3);
10 print chr$(181+(int(rnd(1)+.5)*3)+(ing(rnd(1)+.5)));
10 print chr$(181+(int(rnd(1)+.5)*3));
10 poke 1024+rnd(1)*1000,77.5+rnd(1)
</code></pre>

参考: 10 PRINT[http\://10print.org/](http://10print.org/)

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="1150" height="977" src="/wp-content/uploads/2026/09/01_slide35.png" alt="10 PRINT" class="wp-image-19696" srcset="/wp-content/uploads/2026/09/01_slide35-300x255.png 300w, /wp-content/uploads/2026/09/01_slide35-768x652.png 768w, /wp-content/uploads/2026/09/01_slide35-1024x870.png 1024w, /wp-content/uploads/2026/09/01_slide35.png 1150w" sizes="auto, (max-width: 1000px) 100vw, 1000px" /></figure>

### Hybrids

リアル・プログラマー → ハッカー → アマチュアと来て、次に来るものは何でしょうか? それは、ハイブリッドなプログラマーです。では、ハイブリッド (Hybrid) の意味するものとは何でしょう?

<figure class="wp-block-image"><img loading="lazy" decoding="async" width="818" height="580" src="/wp-content/uploads/2026/09/01_slide37.jpg" alt="‘the carrier’ by patricia piccinini, 2012" class="wp-image-19684" srcset="/wp-content/uploads/2026/09/01_slide37-300x213.jpg 300w, /wp-content/uploads/2026/09/01_slide37-768x545.jpg 768w, /wp-content/uploads/2026/09/01_slide37.jpg 818w" sizes="auto, (max-width: 818px) 100vw, 818px" /></figure>

*‘the carrier’ by patricia piccinini, 2012*

これからは、専業プログラマーの時代ではありません。他に専門をもったプログラマーの時代です。

- アート
- デザイン
- 建築
- 広告
- 統計
- 政治
- 経済
- …etc

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

- [https\://forms.gle/8aNJRNteUGBt3bGE8](https://forms.gle/8aNJRNteUGBt3bGE8)

<figure class="wp-block-image size-large"><img decoding="async" src="https://i0.wp.com/qr.quel.jp/tmp/4202d5c23ca79fbea39c44656923d2f2b55dc389.png?ssl=1" alt=""/></figure>

以上3点です! 締切は次回の授業の前日までとします!
