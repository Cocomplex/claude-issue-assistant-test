# claude-issue-assistant-test

Claude GitHub Issue Assistant の動作確認用サンドボックスリポジトリ。

## 概要

GitHubのIssueコメントに `@claude` と書くと、Claudeがコードやドキュメントを変更し、自動でPRを作成します。

## 使い方

1. Issueを作成する
2. コメントに `@claude` を含めてタスクを指示する
   - 例: `@claude docs/sample.md に「## トラブルシューティング」セクションを追加してください`
3. GitHub Actions が自動起動し、Claudeが変更を加えたPRを作成する
4. PRをレビューしてマージする

## 構成

```
├── README.md                      ← このファイル
├── CLAUDE.md                      ← Claudeへの指示
├── docs/
│   └── sample.md                  ← 変更対象のサンプルドキュメント
└── .github/
    └── workflows/
        └── claude-assistant.yml   ← GitHub Actions ワークフロー
```

## 前提条件

- GitHubリポジトリへの書き込み権限
- GitHub Actions が有効になっていること
- Anthropic API キーが GitHub Secrets に設定されていること (`ANTHROPIC_API_KEY`)

## Claudeにできること

- Issueやコメントの質問に回答する
- コードやドキュメントの変更を実装し、PRを作成する
- コードレビューのフィードバックを提供する
- タスクを分解して段階的に対応する

## Claudeにできないこと

- PRの自動マージ（人間のレビューが必要）
- `.github/workflows/` 配下のファイル変更
- 複数のコメントを投稿すること（既存コメントの更新のみ）
- リポジトリ外のコマンド実行

## 指示の例

```
# ドキュメント追加
@claude docs/sample.md に「## トラブルシューティング」セクションを追加してください

# コードレビュー
@claude このPRのコードをレビューしてください

# 質問
@claude このエラーの原因を教えてください
```

## トラブルシューティング

| 症状 | 対処法 |
|------|--------|
| Claudeが反応しない | GitHub Actions のログを確認する |
| PRが作成されない | `ANTHROPIC_API_KEY` シークレットの設定を確認する |
| エラーが発生する | Issueのコメント欄に表示されたジョブリンクを確認する |

## 注意事項

- このリポジトリはテスト用途のサンドボックスです
- PRは必ず人間がレビューしてからマージしてください
- Claudeへの指示は `CLAUDE.md` で管理されています
