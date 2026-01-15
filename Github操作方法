# 🧑‍💻 Terminal から GitHub にコードを Push する方法

（初心者向け・コピペOK）

このガイドでは次の流れを説明します。

1. 他人のリポジトリを **Clone（コピー）** する
2. 自分の GitHub に **新しいリポジトリを作る**
3. Clone したコードを **自分のリポジトリに Push** する
4. 変更を加えたあとに **git add / commit / push** する

---

## 🔰 前提条件（最初に確認）

* GitHub アカウントを持っている
* Mac / Windows / Linux の **Terminal（または PowerShell）** を使える
* Git がインストールされている

確認方法：

```bash
git --version
```

バージョンが表示されればOK。

---

## ① 他人のリポジトリを Clone する

まず、**元になるリポジトリ（例：先生・先輩・このプロジェクト）を自分のPCにコピー**します。

### 1. GitHubでリポジトリを開く

* 緑の **「Code」** ボタンを押す
* HTTPS のURLをコピー

例：

```
https://github.com/USERNAME/original-repository.git
```

---

### 2. Terminalで Clone

```bash
git clone https://github.com/USERNAME/original-repository.git
```

成功すると：

```text
Cloning into 'original-repository'...
```

と表示されます。

---

### 3. フォルダに移動

```bash
cd original-repository
```

---

## ② 自分の GitHub に新しいリポジトリを作る

次に、**自分専用のリポジトリ**を作ります。

### 1. GitHub → 「New repository」

* Repository name：好きな名前
  例：

  ```
  industry-news-analyzer-yourname
  ```
* **Public / Private** はどちらでもOK
* **Initialize はしない（README等は作らない）**

👉 Create repository

---

## ③ Clone元との接続を切る（重要）

今の状態では、元の人のリポジトリとつながっています。
これを一度削除します。

```bash
git remote -v
```

表示例：

```text
origin  https://github.com/USERNAME/original-repository.git (fetch)
origin  https://github.com/USERNAME/original-repository.git (push)
```

### 削除：

```bash
git remote remove origin
```

---

## ④ 自分の GitHub リポジトリを登録する

### 1. 自分のリポジトリURLをコピー

例：

```
https://github.com/YOURNAME/industry-news-analyzer-yourname.git
```

### 2. 新しい origin を追加

```bash
git remote add origin https://github.com/YOURNAME/industry-news-analyzer-yourname.git
```

確認：

```bash
git remote -v
```

👉 **自分のURL**が出ていればOK。

---

## ⑤ 最初の Push（超重要）

```bash
git branch -M main
git push -u origin main
```

これで：

✅ **元のコードが自分のGitHubにコピーされた状態**
になります。

---

# ✏️ ⑥ コードを変更したあとの基本フロー

ここからは毎回これだけ。

---

## 1. 変更を確認

```bash
git status
```

---

## 2. 変更をステージする

```bash
git add .
```

※「.」は「全部」という意味

---

## 3. コミットする

```bash
git commit -m "update config.yaml for marketing industry"
```

💡 コメントは **何をしたか分かる英語**で書く

良い例：

* `update finance keywords`
* `add new RSS sources`
* `improve dashboard logic`

---

## 4. GitHubにPush

```bash
git push
```

---

## 🎯 最低限覚える3コマンド（試験に出る）

```bash
git add .
git commit -m "your message"
git push
```

これだけでOK。

---

# ❗ よくあるエラーと対処

### 🔸 push できない（認証エラー）

→ GitHub が **Token 認証**を使っています
→ ブラウザでログインが求められたら指示に従う

---

### 🔸 commit できない（名前・メール）

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

# 🎓 このプロジェクトで学生がやっていること（重要）

* 実務と同じ Git フロー
* 自分専用の研究リポジトリを持つ
* 設定（config.yaml）だけで業界分析を作る
* **「使える成果物」をGitHubに残す**

👉 **普通にインターン / 就活で話せる経験**

---

## ✅ 最終チェックリスト

* [ ] clone できた
* [ ] 自分のGitHubにpushできた
* [ ] config.yamlを編集した
* [ ] commit messageが分かりやすい
* [ ] GitHubで変更が見える

---

