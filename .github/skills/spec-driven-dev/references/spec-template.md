# 仕様テンプレート

`docs/SPEC.md` または `docs/specs/<feature-name>.md` を作成する際のテンプレート。

---

## Feature: [機能名]

**Status**: Draft  
**Owner**: [担当エージェントまたは人物]  
**Last Updated**: YYYY-MM-DD  
**Spec File**: `docs/specs/<feature-name>.md`（詳細仕様がある場合）

### Description

[この機能が何をするか。なぜ必要か。ユーザーへの価値は何か。]

### Scope

**含まれるもの（In scope）:**
- 機能A
- 機能B

**含まれないもの（Out of scope）:**
- 機能C（将来バージョンで検討）

### Acceptance Criteria

- [ ] ユーザーが〇〇できる
- [ ] システムが〇〇を正しく処理する
- [ ] 〇〇のエラーケースで適切なメッセージを表示する

### Technical Notes

[実装上の注意点、使用するライブラリ、アーキテクチャ判断など。任意。]

### Dependencies

- Feature: [依存する他の機能名]
- External: [使用する外部サービス・API]

### Open Questions

- [ ] 未解決事項1
- [ ] 未解決事項2

---

## Status の意味

| Status | 意味 |
|---|---|
| `Draft` | 仕様作成中・未承認 |
| `Approved` | ユーザーが確認・承認済み、実装可能 |
| `Implemented` | 全 Acceptance Criteria が実装済み |
| `Deprecated` | 廃止・削除予定 |
