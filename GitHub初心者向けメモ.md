# 初心者向けGitHubメモ

# リポジトリ作成時

## 著作権説明一覧

| ライセンス名        | 特徴                                      | 商用利用 | 改変 | 再配布 | クレジット表記 | コピーレフト       |
|---------------------|-------------------------------------------|----------|------|--------|----------------|--------------------|
| MIT                 | 簡潔で自由度が高い。著作権表示が必要        | ✅       | ✅   | ✅     | ✅             | ❌（なし）         |
| Apache 2.0          | MITに加えて特許使用許諾を明示              | ✅       | ✅   | ✅     | ✅             | ❌（なし）         |
| GPL v3              | 強いコピーレフト。派生物にもGPLが適用される | ✅       | ✅   | ✅     | ✅             | ✅（強い）         |
| LGPL v3             | ライブラリ用。リンクだけならGPL不要         | ✅       | ✅   | ✅     | ✅             | ✅（弱い）         |
| BSD 2-Clause        | MITに似て軽量。告知と免責のみ              | ✅       | ✅   | ✅     | ✅             | ❌（なし）         |
| BSD 3-Clause        | BSD2に名前使用制限追加                     | ✅       | ✅   | ✅     | ✅             | ❌（なし）         |
| MPL 2.0             | 変更部分の公開義務のみの中庸なライセンス     | ✅       | ✅   | ✅     | ✅             | ⚠️（部分的）       |
| Unlicense           | 著作権放棄。完全自由                       | ✅       | ✅   | ✅     | ❌             | ❌（なし）         |
| Creative Commons系  | 文章・画像など用。コードには非推奨          | 条件による | 条件による | 条件による | ✅             | 条件による         |

---


## リポジトリ名の特殊効果

## ✅ GitHub Pagesの「ユーザーページ」の概要

- GitHubの機能で、**HTML/CSS/JSベースの静的サイトを無料でホスティング**できるサービスです。
- 「ユーザーページ」は、特別なリポジトリ名を使って、**アカウント全体の紹介ページ**として公開されます。

### 🔑 特徴的な点

| 項目           | 内容                                         |
|----------------|----------------------------------------------|
| リポジトリ名     | `ユーザー名.github.io`                      |
| 公開URL        | `https://ユーザー名.github.io/`              |
| ルートURL       | ルート（ `/` ）に展開される                  |
| 主な用途        | ポートフォリオ、プロフィール、紹介ページなど |

---

## 🧪 通常の「プロジェクトページ」との違い

| 項目             | ユーザーページ                      | プロジェクトページ                           |
|------------------|-----------------------------------|---------------------------------------------|
| リポジトリ名       | `username.github.io`              | 任意の名前（例：`my-app`）                  |
| 公開URL          | `https://username.github.io/`     | `https://username.github.io/my-app/`        |
| デプロイ先ブランチ | `main` または `master` の `/`     | `gh-pages` ブランチ、または `/docs` フォルダ |
| 用途             | 自己紹介ページ、トップページなど     | アプリ、ライブラリ、ツール紹介など           |

---

## 🧰 作り方（ユーザーページ）

1. GitHubでリポジトリを作成：
   - 名前を **`yourusername.github.io`** にする（自分のアカウント名を使う）

2. `index.html` をコミット（またはJekyllテンプレート使用）

3. `Settings` → `Pages` に移動

4. 「Branch: `main` / root」を選択して保存

5. 数十秒〜数分で **`https://yourusername.github.io/`** に公開されます

---

## ✨ よくある活用例

- エンジニアのポートフォリオサイト
- リンク集やSNSプロフィール集
- ブログ（Jekyll対応）
- 名前入り名刺代わりのトップページ

---

## 📌 注意点

| 注意点                        | 内容                                                         |
|-------------------------------|--------------------------------------------------------------|
| ユーザー名とリポジトリ名は完全一致が必要 | 例：`haradakazutora` なら `haradakazutora.github.io`  |
| 同じアカウントに**1つだけ**   | 複数作ると競合するため、ユーザーページは1つに限られます     |
| URLが `/` ルートになる       | 他のプロジェクトページと重複しないように注意               |

---

## 📄 補足：JekyllやMarkdown対応

- GitHub Pagesは **Jekyll** 対応しており、Markdownファイル（例：`README.md`, `index.md`）も自動変換してくれます
- テーマを設定するだけでブログのような見た目も簡単に実現可能

---

## 「Public（公開）」なリポジトリにおいて、他のユーザーに編集権限を与えないようにする

### publicでも編集権限を与えない方法

1. 🔐 **Collaboratorを追加しない**  
   デフォルトで他人は編集できません（Public＝「閲覧のみ」）

2. 🛡️ **Branch保護ルール（Protected Branches）を設定**  
   たとえ編集者を追加しても、`main` や `master` を守ることができます。

**設定手順：**  
- リポジトリ → `Settings` → `Branches`  
- `Branch protection rules` → 「Add rule」  
- `main` などのブランチ名を指定  
- 以下をチェック：  
  - ✅ "Require pull request reviews before merging"  
  - ✅ "Restrict who can push to matching branches"（必要に応じて）  
  - ✅ "Require status checks to pass before merging"

---

### 🔄 他人が「変更提案」する方法（編集ではない）

🌱 **Fork + Pull Request 方式**  
他のGitHubユーザーは **フォーク（fork）** して自分のコピーを作り、  
そこで編集してから **Pull Request（PR）** を送ってくる形です。  

あなた（リポジトリ所有者）はレビューして「Merge」するか判断できます。

☑️ つまり、「誰でも提案はできるが、マージするのは自分だけ」にできます。

---

## フォークしてPR提出可能、不可能のそれぞれの設定方法

🔑 ポイントは：「フォークそのものはPublicなら誰でも可能。PR提出は、受け取る側の設定とブランチ保護に依存します」

✅ 前提の理解：フォークとPRの関係

| 機能	 | 説明 |
|--------|-----------------------------------------|
| フォーク |	Publicなリポジトリなら誰でも可能（制限不可） |
| PR提出	 |フォーク元にPull Requestを送る操作 |
| マージ権限 |	PRをレビューしてマージできるのは元リポジトリのCollaboratorやOwner |

### 🛠️ PRの提出を「可能」にする設定方法
✅ ① リポジトリを Public に設定する
フォークとPR提出を許可する前提条件

Settings > Danger Zone > 「Change repository visibility」

✅ ② デフォルトブランチ（mainなど）を保護しすぎない
Settings > Branches > Branch protection rules

PRの提出自体をブロックしたくない場合は、以下はONにしない方がよい：
❌ Restrict who can push to matching branches

このチェックを外しておけば、誰でもPRを送ることは可能になります（マージは別）

✅ ③ Pull Requestのレビューは「必須」にしておく（推奨）
Settings > Branches > Protection rules:

✅ "Require pull request reviews before merging"

✅ "Require status checks to pass before merging"

※ PRは受け取るが、自動でマージされないようにするための安全策です。

### ❌ PR提出を「不可能」にする（または制限する）設定方法
✅ 方法①：リポジトリを Private にする
フォーク不可（GitHubの仕様でPrivate repoはフォークできない）

Settings > Danger Zone > Change to Private

✅ 方法②：PR提出を受け取るブランチへのマージを制限
Settings > Branches > Add branch protection rule

✅ "Restrict who can push to matching branches"

許可したユーザー（例：Collaborator）のみPR受け入れ可

✅ 方法③：IssueやPR自体を非推奨にする文言をREADMEに記載
GitHubの仕様上、完全にブロックする方法はない（Publicな場合）

ただし、以下のような記述で非公式に拒否は可能：

**このリポジトリではPRを受け付けていません。ご理解ください。**

🧪 特殊設定：GitHub Enterprise / Organizationの場合
Organization単位で「フォークを無効にする」オプションがある

[Settings] → [Member privileges] → 「Allow forking of private repositories」

📊 まとめ

| やりたいこと	| 方法 |
|----|---|
| フォーク + PR 提出「可能」にする |	リポジトリを Public にし、ブランチ保護は緩めに設定 |
| PR提出「不可 or 制限」 |	Privateにする、ブランチ保護でpushとPR制限 |
|完全に拒否したい	| GitHub上では不可能。READMEで方針を明記する |
**

# トラブル対応

## 🔧 Markdownでうまく表示できない場合の対処ポイントまとめ

- \<h2\>などのHTMLタグ：	**Markdownの\#\# 見出しなどに置き換える**
- 表の前後の空行：	**1行空けるとプレビューが安定しやすい**
- 改行と箇条書き：	**Markdownの記法（-, 1., \#\#など）を使う**

Markdownの整形も自動でやりたい場合は、VSCodeのMarkdown Preview Enhanced拡張や、GitHub Desktopも便利ですよ。
