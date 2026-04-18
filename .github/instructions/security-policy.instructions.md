---
description: "Environment security policy enforcement. Apply when creating environments, adding dependencies, running scripts, or making infrastructure changes. Covers ransomware prevention, license control, 90-day cooldown restrictions."
applyTo: "**"
---

# 環境セキュリティポリシー

## 目的

環境作成・変更時にランサムウェア対策とライセンス統制を標準化し、OWASP Top 10 に準拠したセキュアな開発環境を維持する。

## 必須ルール

1. **スクリプト実行前検証**: 未検証スクリプトの直接実行を禁止する（署名またはハッシュ確認必須）
2. **依存バージョン固定**: 依存ライブラリはバージョンを固定（pin）し、可能な限りハッシュ検証を行う
3. **90日クールダウン制約**: 90日間クールダウン要件があるツール・仕組みを標準利用しない
4. **ライセンス制限**: ライセンス条件が厳しい、または不明瞭な依存は標準利用しない
5. **例外処理**: ルール3・4 の例外は Planner が文書化 → Auditor がリスク評価 → Orchestrator が承認を得てから Executor が実施
6. **変更記録**: 依存追加・環境変更は Recorder がログに残す

## セキュリティチェックリスト（実行前）

- [ ] 使用するスクリプト・バイナリの出所を確認した
- [ ] 依存のライセンスを確認した
- [ ] 90日クールダウン対象でないことを確認した
- [ ] ルール例外が必要な場合は承認フローを経た

## 許可フロー（例外申請）

```
1. Planner が例外理由を文書化（docs/exceptions/EXCEPTION-XXXX.md）
2. Auditor がリスク評価を実施
3. Orchestrator がユーザーに承認依頼（vscode_askQuestions で確認）
4. 承認記録後、Executor が実施
```

## OWASP Top 10 参照

コード実装時は OWASP Top 10 に準拠すること。特に：

- **A01 Broken Access Control**: 権限チェックを実装する
- **A02 Cryptographic Failures**: 機密データは暗号化する
- **A03 Injection**: 入力値を検証・サニタイズする
- **A05 Security Misconfiguration**: デフォルト設定を変更する
- **A09 Logging Failures**: セキュリティイベントをログに記録する
