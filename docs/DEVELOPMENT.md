# 開発手順書

## PR のマージ方法

このプロジェクトでは、GitHub CLI (`gh`) を使用してPRをマージします。

### 基本的なマージコマンド

```bash
gh pr merge <PR_NUMBER> --merge --delete-branch
```

**パラメータ説明:**
- `<PR_NUMBER>`: マージするPRの番号（例：123）
- `--merge`: マージコミットを作成（デフォルト）
- `--delete-branch`: マージ後に対象ブランチを削除

### 使用例

```bash
# PR #123 をマージして、ブランチを削除
gh pr merge 123 --merge --delete-branch
```

### その他のマージ戦略

**Squash マージ:**
```bash
gh pr merge <PR_NUMBER> --squash --delete-branch
```

**Rebase マージ:**
```bash
gh pr merge <PR_NUMBER> --rebase --delete-branch
```

### PR の状態確認

```bash
# PR の詳細情報を表示
gh pr view <PR_NUMBER>

# すべてのオープン PR を一覧表示
gh pr list
```

### PR のレビュー

```bash
# PR をレビュー中としてマーク
gh pr review <PR_NUMBER> --request-changes

# PR を承認
gh pr review <PR_NUMBER> --approve

# コメント付きでレビュー
gh pr review <PR_NUMBER> --comment --body "レビューコメント"
```

### Copilot レビューコメントの取得

**JSON 形式で全レビューコメントを取得:**
```bash
gh pr view <PR_NUMBER> --json reviews
```

**より詳細な情報を取得（レビュー、コメント、判定を含む）:**
```bash
gh pr view <PR_NUMBER> --json reviews,comments,reviewDecisions
```

**Copilot レビューのみをフィルタリング（jq を使用）:**
```bash
gh pr view <PR_NUMBER> --json reviews | jq '.reviews[] | select(.author.login == "copilot")'
```

**整形された JSON を整出力:**
```bash
gh pr view <PR_NUMBER> --json reviews | jq '.'
```

**レビューコメントを CSV 形式で処理:**
```bash
gh pr view <PR_NUMBER> --json reviews --template '{{range .reviews}}{{.author.login}}\t{{.state}}\t{{.body}}\n{{end}}'
```

## 参考資料

- [GitHub CLI Documentation](https://cli.github.com/manual/)
- [gh pr merge](https://cli.github.com/manual/gh_pr_merge)
