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

## 注意事項

- このリポジトリはテスト用途のサンドボックスです
- PRは必ず人間がレビューしてからマージしてください

## 開発者向け情報

### リポジトリのクローン

```bash
git clone https://github.com/Cocomplex/claude-issue-assistant-test.git
cd claude-issue-assistant-test
```

### ローカルでの確認手順（Markdownプレビュー）

- **VS Code**: ファイルを開き、`Ctrl+Shift+V`（macOS: `Cmd+Shift+V`）でプレビューを表示
- **GitHub CLI**: `gh repo view --web` でブラウザ上のリポジトリを確認
- **その他**: `README.md` や `docs/sample.md` は任意のMarkdownビューアで確認可能
