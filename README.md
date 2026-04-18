# my-agents

**仕様駆動（Spec-Driven）開発ハーネス** です。  
このリポジトリをクローンするだけで、仕様先行・オーケストレーション型の GitHub Copilot 開発環境が整います。

## 特徴

- **仕様先行（Spec-First）**: 実装前に必ず仕様を書く。`SPEC.md` が単一真実源
- **オーケストレーション**: `@orchestrator` → `@spec-writer` / `@implementer` / `@reviewer` の専門分業
- **インタラクティブフォローアップ**: 作業完了後に `vscode_askQuestions` でクリック選択または自由記述による次の指示を求める

## クイックスタート

1. このリポジトリをクローンして VS Code で開く
2. `SPEC.md` に作りたい機能の概要を書く（または `/new-feature` を使う）
3. `@orchestrator` に要求を伝える → 仕様確認 → 実装 → レビューが自動で流れる

## エージェント

| エージェント | 役割 |
|---|---|
| `@orchestrator` | 複雑タスクのルーティング（メインエントリポイント） |
| `@spec-writer` | 仕様書の作成・更新 |
| `@implementer` | 仕様に基づく実装 |
| `@reviewer` | 仕様と実装の整合チェック |

## スラッシュコマンド

| コマンド | 目的 |
|---|---|
| `/new-feature` | 新機能の仕様作成から実装まで一貫して進める |
| `/review-spec` | 仕様と実装の整合性を確認する |

## ディレクトリ構成

```text
my-agents/
  SPEC.md                          # プロジェクト仕様（単一真実源）
  docs/
    specs/
      SPEC-TEMPLATE.md             # 詳細仕様テンプレート
  .github/
    copilot-instructions.md        # ハーネス全体ルール
    agents/
      orchestrator.agent.md
      spec-writer.agent.md
      implementer.agent.md
      reviewer.agent.md
    skills/
      spec-driven-dev/             # 仕様先行開発ワークフロー
      followup/                    # 作業後フォローアップ
    instructions/
      followup.instructions.md     # フォローアップ強制（全ファイル）
      spec-consistency.instructions.md  # 仕様整合強制（全ファイル）
    prompts/
      new-feature.prompt.md
      review-spec.prompt.md
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
