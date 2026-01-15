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

### 🧠 キーワード設計の考え方

キーワードは「単語集」ではありません。
**“視点”を定義するもの**です。

👉 自分に問いかけてください：

> * 将来この業界で働くとしたら
> * 上司や投資家は
> * どんなニュースを重要だと言うか？

---

### 📐 設計ルール（必ず守る）

1. カテゴリーは **3〜6個**
2. 1カテゴリー = 1つの関心テーマ
3. 英語のみ（海外ニュース対応）
4. 他カテゴリと意味が被らない

---

### 🧩 基本テンプレ

```yaml
keywords:

  CATEGORY NAME:
    [
      "keyword1","keyword2","keyword3","keyword4","keyword5"
    ]
```

---

## ⑤ 実例①：マーケティング専攻の学生

### 🎯 ゴール

> 将来、**デジタルマーケティング職**として
> プラットフォーム変化と消費者行動を理解したい

```yaml
industry: "Digital Marketing"

use_ai_summary: false
top_n: 5

keywords:

  Consumer behavior:
    [
      "consumer behavior","purchase intent","brand perception",
      "customer journey","user engagement","conversion rate"
    ]

  Platform strategy:
    [
      "google ads","meta ads","tiktok marketing",
      "algorithm change","platform update","ad targeting"
    ]

  Brand & growth:
    [
      "brand strategy","brand loyalty","user acquisition",
      "growth strategy","market penetration"
    ]

  Regulation & privacy:
    [
      "privacy regulation","cookie restriction",
      "data privacy","tracking limitation","gdpr"
    ]
```

📌 **この学生が語れること**

> 「私は広告テクニックよりも、
> プラットフォーム構造と消費者心理の変化を追う設計にしました」

---

## ⑥ 実例②：ファイナンス / 投資志望の学生

### 🎯 ゴール

> S&P500 への投資判断に役立つ
> **マクロ × 企業 × バリュエーション**を追う

```yaml
industry: "US Equity Market"

use_ai_summary: false
top_n: 5

keywords:

  Macro economy:
    [
      "economic growth","recession risk","inflation trend",
      "labor market","consumer spending"
    ]

  Monetary policy:
    [
      "federal reserve","interest rate","rate cut",
      "rate hike","liquidity condition"
    ]

  Valuation & expectations:
    [
      "valuation","forward pe","earnings expectations",
      "multiple expansion","risk premium"
    ]

  Corporate earnings:
    [
      "earnings report","revenue growth","profit margin",
      "guidance update","earnings surprise"
    ]
```

📌 **これ、普通に投資会社の新人研修レベル**

---

## ⑦ sources：情報源（RSS）の設定

```yaml
sources:
  - name: "Source Name"
    rss: "RSS URL"
```

### ガイドライン

* 最初は **3〜6個でOK**
* 大手ニュース + 専門メディアを混ぜる
* 後から増やせる

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
* [ ] 各カテゴリの役割を説明できるか？
* [ ] RSS は１０個以上あるか？
* [ ] RSS は信頼できるか？

---

