---
name: html-generation
description: "HTML generation skill. Use when creating semantic HTML pages or components, accessibility-compliant markup, or lightweight single-file HTML output. Covers structure design, accessibility attributes, and minimal dependency output."
argument-hint: "作成したいHTMLの内容や要件を説明してください"
---

# HTML Generation

## When to Use

- 汎用的な HTML ページやコンポーネントを作成するとき
- アクセシビリティ対応の HTML が必要なとき
- 軽量な単一 HTML ファイルを優先したいとき

## 手順

1. 要件からセマンティックな構造を設計する
   - `<header>`, `<main>`, `<footer>`, `<nav>` などのランドマーク要素を使用する
   - 見出し階層 (`h1`→`h2`→`h3`) を適切に設定する

2. アクセシビリティ属性を付与する
   - 画像: `alt` 属性
   - フォーム: `<label>` と `for` 属性
   - インタラクティブ要素: `aria-label` / `role`
   - カラーコントラスト比 4.5:1 以上

3. 不要な外部依存を避ける
   - CDN 依存を最小化する
   - 軽量な単一 HTML を優先する

4. セキュリティを確認する
   - XSS 対策: ユーザー入力は必要に応じてサニタイズする
   - `<script>` は必要最小限に

## 出力先

- `output/` または指定されたパスに配置する
- ファイル名: `index.html`, `components/*.html`

## アンチパターン

- インラインスタイルの過用
- テーブルレイアウト
- スクリーンリーダーが読めない純粋装飾要素への意味的タグ
