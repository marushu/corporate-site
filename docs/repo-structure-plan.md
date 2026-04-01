# Repository Structure Plan

hibou-web.com を将来的に複数サービス掲載へ拡張していくための、情報設計とディレクトリ構成の整理メモ。

---

## この文書の目的

- `corporate-site` リポジトリを、単一 LP 用ではなく、複数サービスを内包できる構成へ育てる
- 現在は `/before-update/` を主軸にしつつ、将来的に `TOMIO` `SunabaEye` `VTDD` を追加しやすい形にする
- `main` ブランチの `README.md` は総合案内にし、各サービスはディレクトリごとに役割分担する
- 将来的に Codex や VTDD へ渡しやすい構造にする

---

## 基本方針

### 1. main README は総体的な記述にする

`README.md` は単一ページの作業ログではなく、repo 全体の入口として扱う。

載せる内容:

- この repo が何のためのものか
- hibou-web.com 全体の役割
- 現在公開中の主軸ページ
- 将来的に掲載したいサービス
- ディレクトリ構成の説明
- 実装時の運用方針

### 2. 各ページ / サービスはディレクトリ単位で分ける

提案構成:

```txt
/top
/site-contents/top
/site-contents/tomio
/site-contents/sunabaeye
/site-contents/vtdd
/docs
```

※ ユーザー要望では `/top` と `/site-contents/...` を想定しているが、`/top` と `/site-contents/top` のどちらを実体にするかは後で整理してよい。

---

## 提案ディレクトリ構成

### ルート

```txt
README.md
/docs/
/site-contents/
/top/
```

### `/docs`

設計・方針・実装タスク・運用メモを置く。

例:

```txt
/docs/site-restructure-task.md
/docs/repo-structure-plan.md
/docs/content-guidelines.md
/docs/vtdd-handoff-notes.md
```

### `/top`

トップページ専用のコンテンツ方針、コピー案、実装メモを置く。

例:

```txt
/top/README.md
/top/content-draft.md
/top/implementation-notes.md
```

### `/site-contents/top`

トップページに実際に載せる内容の原稿や構造を置く。

### `/site-contents/tomio`

TOMIO 掲載用。

想定内容:

- サービス概要
- 価値提案
- 想定ユーザー
- 導線
- FAQ
- 今後の実装メモ

### `/site-contents/sunabaeye`

SunabaEye 掲載用。

想定内容:

- サービス概要
- 更新前確認の思想
- LP 下書き
- FAQ
- 実運用との差分
- 将来的な AI / API 方向性のメモ

### `/site-contents/vtdd`

VTDD 掲載用。

想定内容:

- 概要説明
- 何を目指すか
- どこまでできているか
- デモ導線の想定
- 将来的な Codex / GitHub / WordPress 連携メモ

---

## 役割分担の考え方

### README.md

総合案内。repo 全体の入口。

### /docs

設計と思考ログ。

### /top

トップページ固有の設計・実装メモ。

### /site-contents/*

公開ページに載せる内容の原稿置き場。

---

## この構造にするメリット

### 1. 今は LP だけでも、将来の追加に耐えやすい

現時点では `/before-update/` が主力だが、後から TOMIO / SunabaEye / VTDD を足しても散らかりにくい。

### 2. Codex に渡しやすい

「どのサービスのどの原稿を見ればよいか」が明確になる。

### 3. VTDD のログ起点にしやすい

- 何を考えたか
- どの原稿を変えたか
- どのページをどう位置づけたか

を追いやすい。

### 4. 将来的に WordPress 側の固定ページ構成とも対応づけしやすい

例:

```txt
/site-contents/sunabaeye -> /sunabaeye/
/site-contents/tomio -> /tomio/
/site-contents/vtdd -> /vtdd/
```

---

## 現時点での批判的整理

この構想は良いが、今すぐ全部作る必要はない。

注意点:

- 情報設計を作ることと、実際に売上が立つことは別
- TOMIO / SunabaEye / VTDD を同時に前面へ出すと、サイトの主題が散る可能性がある
- 当面はトップの主軸を 1 つに絞る方がよい
- 今すぐ売る導線は `/before-update/` ベースで進める方が現実的

つまり、構造は複数サービス対応にしてよいが、公開上の主役は段階的に増やすべき。

---

## WordPress 7.0 + VTDD + 更新の仕組みについて

これは現時点では **アイディアであり、今後の実験テーマ**。

整理すると:

### やりたいこと

- WordPress 7.0 を入れる
- VTDD とつなぐ
- 会話や構成案から、更新やページ変更へつなぐ
- ログも残す

### 現時点の位置づけ

- 今すぐ売るための必須機能ではない
- しかし将来的な差別化や内部運用の武器にはなりうる
- まずは「設計ログを repo に残す」ところから始めるのが現実的

### 批判的に見ると

- 仕組みを先に作ると、売上より実験が先行しやすい
- WordPress 7.0 連携は魅力的だが、検証コストを食いやすい
- 今週中に全部やるのは負荷が高い可能性がある

### 前向きに見ると

- VTDD の思想と今の repo 整理は相性が良い
- 「会話 → 設計ログ → 実装」の流れは、すでに始まっている
- WordPress 7.0 連携は、その先の BUILD レイヤーとして考えると自然

---

## 当面の優先順位

### 優先度 高

1. `/before-update/` を売れる形へ寄せる
2. トップページ差し替え
3. FAQ / JSON-LD 実装
4. repo 構造を整理する

### 優先度 中

5. `/site-contents/sunabaeye` などの雛形を作る
6. 各サービス説明の素案を蓄積する

### 優先度 低（実験枠）

7. WordPress 7.0 + VTDD + 更新フロー実験
8. 会話から実装へつなぐ自動更新の仕組み検証

---

## 次にやるとよいこと

- `README.md` を repo 全体案内へ書き換える
- `/site-contents/` 配下のディレクトリを作る
- 各ディレクトリに README を置く
- まずは `sunabaeye` と `vtdd` の箱だけ作る
- 実際の公開導線は当面 `/before-update/` を主役にする

---

## 結論

- この構成案はアイディアであり、同時にかなり良い情報設計でもある
- 今すぐ全部前に出す必要はないが、repo の設計としては先に切っておいてよい
- WordPress 7.0 + VTDD + 更新は、短期売上の導線ではなく中期の実験テーマ
- まずは「売れる LP」と「整理された repo」を両立させるのがよい
