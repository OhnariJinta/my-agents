---
description: "仕様駆動開発のルールを強制する。Use when starting a new feature, fixing a bug, modifying code, or reviewing implementation. Ensures spec-first workflow."
applyTo: "**"
---

# 仕様整合ルール（Spec-First Enforcement）

## 作業開始前チェックリスト

新しいタスクを開始する前に以下を実行すること：

1. `docs/SPEC.md` を読んで現在の仕様を把握する
2. 対象の機能・変更に対応する仕様エントリが存在するか確認する
3. **存在しない場合**: `@spec-writer` を呼び出すか、自分で仕様エントリを書いてからタスクに着手する
4. **存在する場合**: その仕様に従って実装・修正する

## 作業中のルール

- 実装は常に仕様に従うこと
- 仕様と実装が乖離していることを発見した場合：
  1. ユーザーに報告する
  2. 「仕様を変更すべきか」「実装を修正すべきか」を確認する
  3. **仕様を先に更新**してから実装を修正する
- 仕様にない機能をスコープ拡大で追加しないこと（YAGNI）

## 作業完了後チェックリスト

1. `docs/SPEC.md` の該当機能エントリのステータスと受け入れ基準を更新する
2. 詳細仕様が `docs/specs/` にある場合はそちらも更新する
3. フォローアップポップアップを表示する（`followup.instructions.md` 参照）

## 仕様エントリの書き方

`docs/SPEC.md` に追加する際は以下の形式を使用する：

```markdown
## Feature: [機能名]

**Status**: Draft | Approved | Implemented | Deprecated  
**Last Updated**: YYYY-MM-DD

### Description
[何をするか、なぜ必要か]

### Acceptance Criteria
- [ ] 基準1
- [ ] 基準2

### Implementation Notes
[実装上の注意点・設計判断]
```

より詳細な仕様テンプレートは `docs/specs/SPEC-TEMPLATE.md` を参照。
