---
name: followup
description: "End-of-task user followup skill. Use after completing any work to present the user with context-appropriate next-action choices via interactive popup. Calls vscode_askQuestions tool — NOT plain text output."
user-invocable: false
disable-model-invocation: true
---

# End-of-Task Followup

## 目的

作業完了後に `vscode_askQuestions` ツールを呼び出し、ユーザーが **クリックまたは自由記述** で次のアクションを選択できるポップアップを表示する。

## 重要

> ❌ **禁止**: マークダウンで箇条書きや番号リストとして選択肢を出力する  
> ✅ **必須**: `vscode_askQuestions` ツールを実際に呼び出す

## 手順

1. 直前に完了した作業の種類を特定する
2. 下表から適切な選択肢セットを選ぶ（またはカスタマイズする）
3. `vscode_askQuestions` を以下の形式で呼び出す

```json
{
  "questions": [{
    "header": "nextAction",
    "question": "次に何をしますか？",
    "options": [
      { "label": "...", "description": "（任意の補足説明）" },
      { "label": "その他（自由に入力してください）", "description": "任意の指示を入力できます" }
    ],
    "allowFreeformInput": true,
    "multiSelect": false
  }]
}
```

## 選択肢セット一覧

| 完了した作業 | 推奨選択肢ラベル |
|---|---|
| 仕様作成 | 実装に進む / 仕様をレビューする / 別の仕様を書く |
| 実装完了 | テストを書く / 仕様との整合を確認する / 次の機能を実装する |
| バグ修正 | 修正内容をテストする / 仕様を更新する / 同様のバグを調査する |
| コードレビュー | 指摘を修正する / 仕様を更新する / 別ファイルをレビューする |
| 調査・説明 | 実装に進む / さらに詳しく調べる / 別のトピックを調べる |
| ドキュメント更新 | 実装と整合を確認する / 別ドキュメントを更新する / 変更をコミットする |
