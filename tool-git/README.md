# Git bash

### 目次

## 基礎

```bash
# Gitリポジトリを作成（初期化）
git init

# 既存のリモートリポジトリをクローン
git clone [URL]

# ステータスの確認（何が変わったか）
git status

# 差分の確認
git diff

# コミット履歴の表示
git log

# リモートリポジトリのURLを確認
git remote -v

# リモートリポジトリへプッシュ（アップロード）
git push origin [branch_name]

# リモートからプル（取得・マージ）
git pull origin [branch_name]

# ブランチの作成
git branch [branch_name]

# ブランチの切り替え
git checkout [branch_name]

# ブランチを作成して切り替え
git checkout -b [branch_name]

# マージ（ブランチを統合）
git merge [マージしたいブランチ名]
```