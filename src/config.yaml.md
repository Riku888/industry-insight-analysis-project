# 🧭 config.yaml 設計ガイド

**― 自分の業界分析ツールを作るために ―**

このページは、
**このニュース分析ツールを使う学生が、自分の関心業界に合わせて `config.yaml` を設計するためのガイド**です。

コードを書く必要はありません。
必要なのは「考える力」だけです。

---

## 🎯 この config.yaml の役割

`config.yaml` は、このツールにとって **「思考の設計図」**です。

* どの業界を分析するのか
* どんなニュースを重要だと考えるのか
* どんな視点でトレンドを捉えたいのか

これらを **明示的に定義**します。

---

## 🧱 全体構造（まずは全体像）

```yaml
industry: "YOUR INDUSTRY NAME"

use_ai_summary: false
top_n: 5

keywords:
  CATEGORY 1:
    [ "keyword1","keyword2", ... ]

  CATEGORY 2:
    [ "keyword1","keyword2", ... ]

sources:
  - name: "Source Name"
    rss: "RSS URL"
```

以下、この各パートを **1つずつ**解説します。

---

## ① industry：分析対象の業界を決める

```yaml
industry: "YOUR INDUSTRY NAME"
```

### 🔹 何を書く？

* 自分が **研究したい / 働きたい / 投資したい** 業界
* ニュースを見る「目的」が想像できる名前

### ❌ 悪い例

* `"Technology"`（広すぎる）
* `"Business"`（目的が不明）

### ✅ 良い例

* `"Cybersecurity"`
* `"US Equity Market"`
* `"Digital Marketing"`
* `"AI & Semiconductors"`
* `"Consumer Tech"`

👉 **「この業界で意思決定する人は、何を気にするか？」が浮かぶ名前にする**

---

## ② use_ai_summary：AI要約を使うか

```yaml
use_ai_summary: false
```

* `false`：おすすめ（まずは自分で傾向を見る）
* `true`：慣れてきたらON

📌 **Next Abroadの学習目的では、最初は false 推奨**

---

## ③ top_n：毎日チェックするニュース件数

```yaml
top_n: 5
```

### ガイドライン

* **5〜7件**がベスト
* 多すぎると読まなくなる
* 「毎日続けられる量」を基準に

---

## ④ keywords：分析の核（最重要）

ここが **このプロジェクトの一番大事な部分**です。

---

### 🧩 キーワード設計のルール
* **1カテゴリ = 50キーワード以上**
* 英語のみ
* 他カテゴリと意味が被らない
* 単語だけでなく「フレーズ」も含める

### なぜ50語以上？

理由は明確です：

1. ニュース表現は多様
2. 同じ意味でも言い方が違う
3. 少ないと **分類精度が落ちる**
4. 実務では「広く拾って、後で判断」

👉 **これは検索エンジン的発想**

### 🤖 キーワードを作るためのAIプロンプト（超重要）

以下は **学生がそのまま使っていいサンプルプロンプト**です。

---

### 🔹 汎用テンプレ（コピペOK）

```text
You are a professional industry analyst.

I am building a news monitoring tool using RSS feeds.
The goal is to classify daily news articles into meaningful categories.

Industry:
[WRITE YOUR INDUSTRY]

Category:
[WRITE ONE CATEGORY NAME]

Task:
Generate at least 50 English keywords and phrases that are:
- Commonly used in real news articles
- Relevant to this category in a professional context
- Likely to appear in headlines or article bodies
- Not overlapping with other categories

Include:
- Single words
- Multi-word phrases
- Industry-specific terminology
- Policy, business, and market expressions if relevant

Do NOT include explanations.
Output as a simple comma-separated list.
```
### 🧩 基本テンプレ

```yaml
keywords:

  CATEGORY NAME:
    [
      "keyword1","keyword2","keyword3","keyword4","keyword5"
    ]
```
---

### 🔹 具体例（ファイナンス × マクロ経済）

```text
Industry:
US Equity Market

Category:
US macro & economy

Task:
Generate at least 50 English keywords and phrases that are commonly used in real financial news articles related to the US macroeconomic environment.
```

---

### 🔹 具体例（マーケティング × 消費者行動）

```text
Industry:
Digital Marketing

Category:
Consumer behavior

Task:
Generate at least 50 English keywords and phrases related to consumer behavior and decision-making, as used in marketing and business news.
```

---

### ✅ 出力されたらやること（超重要）

AIの出力を：

1. そのまま使わない
2. 1つずつ目で見る
3. 「これはニュースで見るか？」と自問
4. 不要なものを削除
5. 必要なら自分で追加

👉 **最終判断は人間**

---

## ⑦ sources：情報源（RSS）の設定 📡 RSSとは何か？どうやって見つけるのか

### RSSとは？

**RSS（Really Simple Syndication）**とは、
Webサイトが **「新着記事の一覧を自動配信する仕組み」**です。

このツールでは：

* Webサイトを毎日巡回する代わりに
* RSSを使って **新着ニュースだけを自動取得**します

📌 **重要**

> RSSは「スクレイピング」ではありません
> → サイト側が *公式に公開している* 正規の配信手段です

---

### 🧠 なぜRSSを使うのか？

実務では：

* 投資家
* マーケター
* リサーチャー
* コンサルタント

全員が **RSS / ニュースアグリゲーション**を使っています。

理由は単純：

* 情報の取りこぼしを防げる
* 毎日同じ条件で情報が入る
* バイアスが減る

👉 **このツールは「実務の情報収集フロー」を学生用に落としたもの**

---

### 🔍 RSSを見つける3つの方法（重要）

### 方法①：サイト名 + RSS で検索（一番簡単）

Googleでこう検索：

```
Reuters RSS
Bloomberg RSS
site:nikkei.com RSS
```

👉 多くの場合：

* `/rss`
* `/feed`
* `/feeds/posts/default`

のようなURLが見つかります。

---

### 方法②：Google News RSS を使う（超おすすめ）

Google News は **検索結果そのものをRSS化**できます。

#### 例：

「Apple × AI」に関するニュースだけ欲しい場合：

```
https://news.google.com/rss/search?q=Apple+AI&hl=en-US&gl=US&ceid=US:en
```

#### site指定も可能：

```
https://news.google.com/rss/search?q=cybersecurity+site:reuters.com
```

📌 **初心者はこれだけでもOK**
→ 信頼できるメディアだけを抽出できる

---

### 方法③：サイトのフッターを見る（中級者）

Webサイトの下の方に：

* RSS
* Feed
* XML

と書かれたリンクがある場合があります。

---

### 🇯🇵 日本メディアにもRSSはある？

あります。普通にあります。

### 例：

* 日本経済新聞（条件付き）
* NHK
* ITmedia
* ZDNet Japan
* 日経クロステック

📌 **ただし注意**
日本語記事は：

* 見出しが短い
* 英語キーワードと混ざらない

👉 **このツールでは英語RSS推奨**（世界標準）

---

### 🗂 sources に入れるときの考え方

```yaml
sources:
  - name: "Reuters"
    rss: "https://www.reuters.com/rssFeed/businessNews"
```

### 良い構成

* 📰 **一般ニュース（1–2）**
* 🧠 **専門メディア（2–4）**
* 🏢 **企業公式ブログ（任意）**

---

```yaml
sources:
  - name: "Source Name"
    rss: "RSS URL"
```

### ガイドライン

* 大手ニュース + 専門メディアを混ぜる

### 例（ファイナンス）

```yaml
sources:
  - name: "Reuters"
    rss: "https://www.reuters.com/rssFeed/businessNews"

  - name: "Bloomberg"
    rss: "https://www.bloomberg.com/feed/podcast/etf-report.xml"

  - name: "Yahoo Finance"
    rss: "https://feeds.finance.yahoo.com/rss/2.0/headline?s=%5EGSPC"
```

---

## 🧠 最後に：この課題で一番大事なこと

正解はありません。

評価されるのは：

* なぜこの業界なのか
* なぜこのカテゴリなのか
* なぜこのキーワードなのか

👉 **「自分なりの設計理由を説明できるか」**

それが、このプロジェクトのゴールです。

---

## 🏁 チェックリスト（提出前）

* [ ] industry は具体的か？
* [ ] カテゴリは 8 個以上あるか？
* [ ] 各カテゴリ50語以上ある
* [ ] 各カテゴリの役割を説明できるか？
* [ ] RSS は１０個以上あるか？
* [ ] RSS は信頼できるか？
* [ ] なぜこの情報を追うのか語れる

---

