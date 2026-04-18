# my-agents

汎用タスク向けの **AIハーネス雛形** です。  
subAgentオーケストレーション、5ペルソナ、セキュアな環境作成ポリシー、拡張可能な agent/skill レジストリ、プロジェクト構成管理テンプレートを提供します。

## 含まれる要素

- subAgent機能を使うオーケストレーション定義
- ペルソナ:
  - Orchestrator
  - Planner
  - Executor
  - Auditor
  - Recorder
- 環境作成時ポリシー（ランサムウェア対策、ライセンス/90日クールダウン制約）
- SKILL:
  - HTML作成
  - SVG作成
- 汎用タスク実行テンプレート
- agent/skill の成長（追加）に対応するレジストリ
- 構成管理フォルダ雛形（input/output/scripts/docs/logs）

## ディレクトリ

```text
harness/
  agents/
  orchestration/
  policies/
  registry/
  skills/
  tasks/
project-template/
  input/
  output/
  scripts/
  docs/
  logs/
```

## 使い方

1. `harness/orchestration/subagent-orchestration.yaml` を起点に、タスクを5ペルソナへ分解します。
2. `harness/tasks/task-template.yaml` をコピーして実行計画を作成します。
3. 新しい agent/skill は `harness/registry/*.yaml` に登録します。
4. 環境作成時は `harness/policies/environment-security-policy.md` の承認手順に従ってください。

## セキュリティ方針（要点）

- 90日以上のクールダウンが必要な手順/依存はデフォルト禁止
- 厳しい/不明確ライセンスの依存はデフォルト禁止
- 例外利用は **事前に明示的な許可取得が必須**
- 依存追加時は最小権限・ピン留め・ハッシュ検証・監査ログ記録を行う
