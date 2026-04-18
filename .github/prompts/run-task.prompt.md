---
description: "汎用タスクを5ペルソナパイプラインで実行する。Use when starting a generic task that requires planning, execution, audit, and recording (intake → plan → execute → audit → record → close)."
name: "汎用タスク実行"
agent: "agent"
tools: [read, edit, search, execute, agent, todo]
argument-hint: "実行したいタスクの目的と入力データを説明してください"
---

# 汎用タスク実行プロンプト

以下の 5 ペルソナパイプラインでタスクを実行する：

```
intake（orchestrator）
  ↓
plan（@planner）
  ↓
execute（@executor）
  ↓
audit（@auditor）
  ↓
record（@recorder）
  ↓
close（orchestrator）
```

## パイプライン手順

1. **Intake**: タスク目的・入力・受け入れ基準を整理する
2. **Plan**: `@planner` に委譲して execution_plan を作成する
3. **Execute**: `@executor` に委譲して deliverables を作成する
4. **Audit**: `@auditor` に委譲してセキュリティ・品質・ライセンスを確認する
5. **Record**: `@recorder` に委譲して実行ログを `logs/` に保存する
6. **Close**: 完了サマリーを出力し、`vscode_askQuestions` でフォローアップを行う

## セキュリティ確認

セキュリティポリシー（`.github/instructions/security-policy.instructions.md`）に違反する操作は事前に承認を取ること。

## タスク内容

{{ input }}
