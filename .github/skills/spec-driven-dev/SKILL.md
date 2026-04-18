---
name: spec-driven-dev
description: "Spec-driven development workflow. Use when starting a new feature, updating requirements, checking spec-code consistency, or reviewing what has been built. Enforces spec-first: write spec before writing code. Use for specification templates and consistency check procedures."
argument-hint: "実行したいアクション: new-feature / update-spec / consistency-check"
---

# Spec-Driven Development

仕様先行開発のワークフロースキル。コードを書く前に仕様を書く。

## いつ使うか

- 新機能を開始するとき
- 仕様と実装の整合を確認したいとき
- 要件を文書化するとき
- 何が実装済みか確認するとき

## 手順

### A. 新機能を開始する

1. `docs/SPEC.md` を読んで既存エントリを把握する
2. [仕様テンプレート](./references/spec-template.md) を参照して Feature エントリを作成する
3. ユーザーに仕様を確認してもらう（Status: Draft → Approved）
4. 承認後、実装に進む
5. 実装完了後に `docs/SPEC.md` の受け入れ基準を更新する（Status: Implemented）

### B. 整合チェックを実行する

1. `docs/SPEC.md` の対象 Feature エントリを読む
2. 実装ファイルを読む
3. [整合チェックガイド](./references/consistency-check.md) に従って比較する
4. 乖離をレポートする

### C. 仕様を更新する

1. 変更点を `docs/SPEC.md` に反映する
2. `Last Updated` フィールドを更新する
3. 関連する `docs/specs/` ファイルも更新する

## リソース

- [仕様テンプレート](./references/spec-template.md)
- [整合チェックガイド](./references/consistency-check.md)
