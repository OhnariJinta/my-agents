---
description: "仕様と実装の整合を確認する。Use when you want to audit that the code matches the specification, or check acceptance criteria completion."
name: "仕様整合チェック"
agent: "agent"
tools: [read, search, todo]
argument-hint: "チェック対象の Feature 名または変更ファイルを指定してください"
---

# 仕様整合チェックプロンプト

以下の手順で仕様（docs/SPEC.md）と実装の整合を確認する。

## 手順

1. `docs/SPEC.md` を読む
2. `docs/specs/` 配下の詳細仕様ファイルがあれば読む
3. `.github/skills/spec-driven-dev/references/consistency-check.md` に従ってチェックを実行する
4. 結果をレポート形式で出力する
5. `vscode_askQuestions` でフォローアップを行う：
   - 「不整合を修正する（@implementer に委譲）」
   - 「仕様を更新する（@spec-writer に委譲）」
   - 「別の Feature をチェックする」
   - 「その他（自由に入力してください）」

## チェック対象

{{ input }}
