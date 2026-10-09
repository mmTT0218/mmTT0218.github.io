# 申 泰明 — 研究業績・ポートフォリオサイト

Hugo Blox の Academic CV テンプレートをもとに，日英切り替えに対応させた
研究業績＋ポートフォリオサイトです。GitHub Pages で無料公開できます。

- 日本語版: `/`（既定）
- 英語版: `/en/`
- 右上の言語メニューで切り替わります。

---

## 1. 公開までの手順

### 1.1 リポジトリを作る

GitHub で新しいリポジトリを作成します。URL は名前で決まります。

GitHub ユーザ名は `mmTT0218` のため，リポジトリ名によって公開URLが変わります。

| リポジトリ名 | 公開URL | 備考 |
|---|---|---|
| `mmTT0218.github.io` | `https://mmtt0218.github.io/` | 推奨。現在の設定はこちら |
| `Myong.github.io` | `https://mmtt0218.github.io/Myong.github.io/` | リポジトリ名がURLに重ねて入る |
| `homepage` など | `https://mmtt0218.github.io/homepage/` | |

`<ユーザ名>.github.io` 形式（ユーザサイト）は，GitHub のユーザ名と完全に一致する
名前のリポジトリでしか成立しません。`Myong.github.io` という名前にしても，
ユーザ名が `mmTT0218` である限り通常のプロジェクトサイト扱いになり，
リポジトリ名がURLのパスに入ります。

リポジトリ名を変える場合は `config/_default/hugo.yaml` の `baseURL` も
あわせて書き換えてください（GitHub Actions でのビルド時は自動設定されるため，
この値が効くのはローカル確認時のみです）。

### 1.2 ファイルを push する

```bash
cd <このフォルダ>
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<ユーザ名>/<リポジトリ名>.git
git push -u origin main
```

### 1.3 GitHub Pages を有効にする

リポジトリの **Settings → Pages → Build and deployment → Source** を
**GitHub Actions** に設定します。

これだけで `.github/workflows/deploy.yml` が走り，数分で公開されます。
以降は `main` に push するたびに自動で再公開されます。

> `baseURL` は Actions 側で自動設定されるため，`config/_default/hugo.yaml` の
> `baseURL` はローカル確認用の値のままで構いません。

---

## 2. 手元で確認する

```bash
npm install          # 初回のみ
npx hugo server      # http://localhost:1313/ で確認
```

Hugo 本体（extended 版）が必要です。未インストールなら
<https://gohugo.io/installation/> から導入してください。

**バージョンについて**: 現時点で Hugo 0.162.0 はテーマ側の不具合により
ビルドに失敗します。動作確認済みの **0.161.1** を `hugoblox.yaml` に固定しています。

---

## 3. どこを書き換えるか

プロフィール・業績は記入済みです。**`[要確認]`** と書かれた箇所だけ，
正式名称などをご確認ください。以下で一覧できます。

```bash
grep -rn "要確認" config content data
```

雛形のまま残してあるページ（プロジェクト／学会発表／お知らせ）には `XXXXX` が
入っています。これらは `draft: true` が付いているため公開されません。

```bash
grep -rln "XXXXX" content
```

### 3.1 プロフィール

| ファイル | 役割 |
|---|---|
| `data/authors/me.yaml` | 共通＋英語。リンク・日付・レベルなど翻訳不要な項目もここ |
| `data/ja/authors/me.yaml` | 日本語で上書きしたい項目だけを書く |

日本語側に書いた項目が英語側の値を上書きします。
**注意**: `education` / `experience` / `skills` などの配列は丸ごと置き換わるため，
日本語で表示したい場合は配列全体を日本語ファイルに書いてください。

### 3.2 サイト全体の設定

| ファイル | 役割 |
|---|---|
| `config/_default/hugo.yaml` | `baseURL`，既定言語 |
| `config/_default/languages.yaml` | 言語ごとのサイト説明 |
| `config/_default/menus.ja.yaml` | 日本語のナビゲーション |
| `config/_default/menus.en.yaml` | 英語のナビゲーション |
| `config/_default/params.yaml` | サイト名，配色，SEO，アナリティクスなど |

### 3.3 トップページ

| ファイル | 役割 |
|---|---|
| `content/_index.md` | 日本語トップ（表示する節の並び） |
| `content/_index.en.md` | 英語トップ |

### 3.4 差し替えるファイル

| ファイル | 内容 |
|---|---|
| `assets/media/authors/me.png` | プロフィール写真。IDW ’25 会場の写真を正方形に切り出したものを設定済み |

CV を配布する場合は `static/uploads/cv.pdf` を置き，`content/_index.md` と
`content/_index.en.md` でコメントアウトしてある `button:` ブロックを有効にしてください
（現在はボタン自体を非表示にしています）。

各業績フォルダの `featured.png` がカードのサムネイルです。3件とも設定済みで，
図が切れないよう 16:9（1600×900）の白背景に収めてあります。
差し替える場合も同じ比率にすると，カード内でトリミングされません。

---

## 4. 記事・業績の増やし方

1件につき1フォルダを作り，その中に日本語版 `index.md` と英語版 `index.en.md` を置きます。
画像やPDFは同じフォルダに置けば**日英で共用**されます（二重に置く必要はありません）。

```
content/publications/idw2025/
├── index.md        ← 日本語版
├── index.en.md     ← 英語版
├── cite.bib        ← BibTeX（「引用情報」ボタンから配布される）
├── featured.png    ← サムネイル（16:9 推奨）
└── paper.pdf       ← 本文PDF（任意）
```

雛形として以下を用意しています。フォルダごとコピーして使ってください。

### 記入済みの業績

| フォルダ | 内容 |
|---|---|
| `content/publications/3dmt2025/` | 立体メディア技術研究会（3DMT），2025年10月 |
| `content/publications/idw2025/` | IDW ’25，2025年12月（主要業績） |
| `content/publications/smc2026/` | 空間メディアコンファレンス2026，2026年7月（主要業績） |

`index.md` の `featured: true` を付けたものがトップの「業績」カードに表示されます。
現在は3件とも `featured: true` にしてあります。トップページは「業績」（カード）と
「文献リスト」（引用形式）の2段構成です。片方だけでよければ，`content/_index.md` /
`_index.en.md` の該当ブロックを削除してください。

### 雛形（`draft: true` のため非公開）

| フォルダ | 用途 |
|---|---|
| `content/projects/sample-project/` | ポートフォリオ項目 |
| `content/events/sample-talk/` | 学会発表・講演を業績とは別枠で出す場合 |
| `content/blog/hello/` | お知らせ |

内容を書いたら `draft: true` の行を削除し，`config/_default/menus.ja.yaml` と
`menus.en.yaml` の該当するメニュー項目のコメントを外してください。
トップページに一覧を出す場合は `content/_index.md` / `_index.en.md` の
コメントアウトされたブロックも有効にします。

---

## 5. 日本語と英語を入れ替えるには

英語を既定（`/`）にしたい場合は次の2点を変更します。

1. `config/_default/hugo.yaml` の `defaultContentLanguage: ja` を `en` に変更
2. 各コンテンツのファイル名を入れ替える
   （`index.md` ↔ `index.en.md`，`index.ja.md` を作る形になります）

メニューの URL（`menus.*.yaml`）も合わせて修正してください。

---

## 6. ワークフローについて

| ファイル | 内容 |
|---|---|
| `.github/workflows/deploy.yml` | push のたびにビルドして GitHub Pages へ公開 |
| `.github/workflows/build.yml` | ビルド本体（Pull Request の検証にも使われる） |
| `.github/workflows/upgrade.yml` | テーマの更新 PR を毎週作成（不要なら削除可） |
| `.github/workflows/import-publications.yml` | BibTeX から業績ページを自動生成（**手動実行のみ**） |

`import-publications.yml` は `index.md` を自動生成するため，
そのまま自動実行すると日本語版が英語の内容で上書きされます。
このため push による自動実行は無効にしてあります。
使わないのであればファイルごと削除して構いません。

---

## 7. 参考

- Hugo Blox ドキュメント: <https://docs.hugoblox.com/>
- Hugo 多言語機能: <https://gohugo.io/content-management/multilingual/>
- テンプレート本体: <https://github.com/HugoBlox/hugo-theme-academic-cv>

---

## 8. 現状のメモ

- 日本語の表記は「回転ズレ」に統一しています（論文の正式タイトルのみ，出典どおり「回転誤差」のままです）。
- IDW ’25 は国際会議の発表のため，日本語版サイトでも原題（英語）のまま掲載しています。
- 「興味・関心」欄は項目が未指定のため空（`interests: []`）にしてあります。キーワードを入れると表示されます。
- 職歴は履歴書に「なし」とあったため省略しています。
- 高等学校の学歴は，研究者向けサイトでは省略するのが一般的なため載せていません（`data/ja/authors/me.yaml` のコメント参照）。
- スキル欄に `level: 1`〜`5` を足すと習熟度バーが表示されます。自己評価になるため，こちらでは数値を入れていません。
- 運転免許は業績サイトの性格上，受賞・資格欄から外しています。
- 履歴書に記載のあった住所・電話番号・生年月日・個人用メールアドレスは，公開サイトには載せていません。連絡先は大学のメールアドレスのみにしています。
