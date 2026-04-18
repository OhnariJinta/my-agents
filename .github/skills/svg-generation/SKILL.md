---
name: svg-generation
description: "SVG generation skill. Use when creating vector graphics, diagrams, icons, or illustrations. Covers viewBox portability, minimal path definitions, and readable/editable SVG output."
argument-hint: "作成したいSVGの内容（アイコン・図解・ダイアグラム等）を説明してください"
---

# SVG Generation

## When to Use

- アイコン・ロゴ・図解・フローチャートを SVG で作成するとき
- 拡大縮小に対応した vector graphics が必要なとき
- 編集しやすいSVGコードを出力したいとき

## 手順

1. **viewBox で可搬性を確保する**
   ```xml
   <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
   ```
   - `width`/`height` は固定しない（CSS や親要素に委ねる）

2. **パス・図形を必要最小限で定義する**
   - 複雑なパスより単純な `<rect>`, `<circle>`, `<line>`, `<polygon>` を優先する
   - 繰り返し要素には `<use>` と `<defs>` を活用する

3. **装飾より可読性・編集容易性を優先する**
   - ID と class を意味的に命名する（例: `#icon-close`, `.fill-primary`）
   - コメントでセクションを区切る

4. **アクセシビリティを確保する**
   ```xml
   <svg role="img" aria-label="説明">
     <title>SVGの説明</title>
   </svg>
   ```

## 出力先

- `output/` または指定されたパスに配置する
- ファイル名: `assets/*.svg`, `diagrams/*.svg`

## アンチパターン

- `width`/`height` の絶対値固定（レスポンシブ対応不可）
- 過度に複雑なパスデータ（Figma/Illustrator からの直接エクスポートそのまま）
- `<script>` を SVG 内に埋め込む（XSS リスク）
