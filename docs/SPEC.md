# Project Specification

**Project**: my-agents  
**Created**: 2026-04-18  
**Status**: Active

## Overview

GitHub Copilot 仕様駆動（Spec-Driven）開発ハーネス。このリポジトリをクローンするだけで、仕様先行・オーケストレーション型の Copilot 開発環境が整う。

## Architecture

### Agents

| Agent | 役割 | モード |
|---|---|---|
| `@orchestrator` | 全体調整・ルーティング | A（仕様駆動）/ B（汎用） |
| `@spec-writer` | 仕様書作成・更新 | A |
| `@implementer` | 仕様に基づく実装 | A |
| `@reviewer` | 仕様と実装の整合チェック | A |
| `@planner` | 要件分解・実行計画作成 | B |
| `@executor` | 実行計画に沿ったタスク実行 | B |
| `@auditor` | 品質・セキュリティ・ライセンス監査 | B |
| `@recorder` | 実行履歴と意思決定の記録 | B |

### Skills

| Skill | 目的 |
|---|---|
| `spec-driven-dev` | 仕様先行開発ワークフロー |
| `followup` | 作業後インタラクティブフォローアップ |
| `html-generation` | セマンティック HTML 生成 |
| `svg-generation` | ベクター SVG 生成 |

### Instructions（常時適用）

| ファイル | 目的 |
|---|---|
| `followup.instructions.md` | `vscode_askQuestions` ツール呼び出し必須化 |
| `spec-consistency.instructions.md` | 仕様先行ルール強制 |
| `security-policy.instructions.md` | 環境セキュリティ・OWASPポリシー適用 |

### Prompts（スラッシュコマンド）

| コマンド | 目的 |
|---|---|
| `/new-feature` | 新機能の仕様作成から実装まで |
| `/review-spec` | 仕様と実装の整合確認 |
| `/run-task` | 5ペルソナパイプラインで汎用タスク実行 |

---

## Features

## Feature: Spec-Driven Development Harness

**Status**: Implemented  
**Last Updated**: 2026-04-18

### Description

仕様先行開発を強制するハーネス。全ての実装は仕様（SPEC.md）に対応するエントリが存在することを前提とする。

### Acceptance Criteria

- [x] Orchestrator が仕様を確認してからスペシャリストを呼び出す
- [x] Spec Writer が SPEC.md に準拠した仕様エントリを作成する
- [x] Implementer が仕様を読んでから実装を開始する
- [x] Reviewer が仕様と実装の整合性を報告する
- [x] 仕様テンプレート（SPEC-TEMPLATE.md）が利用可能

### Implementation Notes

- `copilot-instructions.md` で全体ルールを定義
- `instructions/spec-consistency.instructions.md` で自動適用
- `docs/specs/SPEC-TEMPLATE.md` がフォーマット基準

---

## Feature: End-of-Task Interactive Followup

**Status**: Implemented  
**Last Updated**: 2026-04-18

### Description

作業完了後に `vscode_askQuestions` ツールを呼び出し、ユーザーがクリックまたは自由記述で次のアクションを選択できるインタラクティブポップアップを表示する。テキストによる番号付き選択肢出力は禁止。

### Acceptance Criteria

- [x] 作業完了ごとに `vscode_askQuestions` ツールが呼び出される
- [x] 選択肢は直前の作業に応じてカスタマイズされる
- [x] 最後の選択肢は必ず「その他（自由に入力してください）」
- [x] `allowFreeformInput: true` で自由記述も常時可能
- [x] 作業途中では呼び出さない

### Implementation Notes

- `instructions/followup.instructions.md`（`applyTo: "**"`）で全ファイルコンテキストに適用
- `skills/followup/SKILL.md` で選択肢セットを参照可能
- ユーザーレベルの instruction（`~/.../instructions/`）でも同様のルールを設定推奨
