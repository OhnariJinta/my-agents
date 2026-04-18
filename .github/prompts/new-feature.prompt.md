---
description: "新機能の仕様を作成してから実装に進む。Use when starting a new feature from scratch."
name: "新機能を開始する"
agent: "agent"
tools: [read, edit, search, agent, todo]
argument-hint: "実装したい機能の概要を説明してください"
---

# 新機能開始プロンプト

以下の手順でユーザーが要求する機能の仕様を作成し、実装に進む。

## 手順

1. `docs/SPEC.md` を読んで既存の機能エントリと重複がないか確認する
2. `docs/specs/SPEC-TEMPLATE.md` を読んでフォーマットを把握する
3. ユーザーの要求に基づいて Feature エントリの草案を作成する
4. `docs/SPEC.md` に Draft エントリを追加する
5. 作成した仕様をユーザーに提示し、`vscode_askQuestions` で確認を求める：
   - 「この仕様で実装に進む」
   - 「仕様を修正する」
   - 「受け入れ基準を追加・変更する」
   - 「その他（自由に入力してください）」
6. 承認後、`@implementer` に実装を委譲する

## ユーザーの要求

{{ input }}
