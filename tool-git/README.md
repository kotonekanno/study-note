<!-- omit in toc -->
# Gitコマンド

<!-- omit in toc -->
### 目次

- [git branch](#git-branch)
- [git switch](#git-switch)
- [git checkout](#git-checkout)
- [git merge](#git-merge)
- [git reset](#git-reset)

## git branch

```bash
# ブランチ一覧を表示
git branch

# 新規ブランチを作成
git branch <branch>

# ブランチを削除（マージ済みのみ、強制ではない）
git branch -d <branch>

# ブランチを強制削除
git branch -D <branch>

# ブランチ名を変更
git branch -m <old-branch> <new-branch>

# 現在のブランチのブランチ名を変更
git branch -m <new-branch>

# ブランチの詳細（最新コミット含む）を表示
git branch -v

# リモート含めて全てのブランチを表示
git branch -a

# リモートブランチのみ表示
git branch -r

# 指定コミットを含むブランチを調べる
git branch --contains <commit-ish>

# マージされていないブランチを表示
git branch --no-merged [<commit|branch>]

# マージ済みのブランチを表示
git branch --merged [<commit|branch>]
```

## git switch

```bash
# 既存ブランチに切り替え
git switch <branch>

# 新規ブランチを作成して切り替え
git switch -c <branch>

# 特定コミットからブランチを作る
git switch -c <branch> <commit>

# 直前のブランチに戻る
git switch -

# 作業内容を破棄して強制切替
git switch --discard-changes <branch>

# 特定コミットに切り替え
git switch --detach <commit>
```

## git checkout

```bash
# 既存ブランチに切り替え
git checkout <branch>

# 新規ブランチを作成して切り替え
git checkout -b <branch>

# 過去のコミットやタグに移動
git checkout <commit>

# ファイルを直前のコミット状態に戻す
git checkout -- <file>

# リモートブランチを元にローカルブランチ作成
git checkout -b <local> origin/<remote>
```

## git merge

```bash
# 他ブランチを現在のブランチへ統合
git merge <branch>

# 自動コミットせず内容確認
git merge --no-commit <branch>

# Fast-fowardを無効化（常にマージコミットを作る）
git merge --no-ff <branch>

# マージ内容の統合を自動で上書き
# （コンフリクト時の優先方向を指定）
git merge -X ours <branch>
git merge -X theirs <branch>

# コンフリクト発生時にマージ中断
git merge --abort
```

1. Fast-foward merge（早送りマージ）
   - 対象ブランチの変更が一方向的（分岐していない）な場合、自動的に履歴を早送り
   - 新しいマージコミットは作られない
   - 履歴が線形になる
2. 3-way merge（通常のマージ）
   - ブランチが分岐して別々に進んでいた場合、共通の祖先コミットを起点に差分を統合
   - マージコミット（両方の履歴をまとめるコミット）が新たに作成される
3. コンフリクト発生
   - 両方のブランチで同じ箇所が変更された場合、Gitが自動で統合できず手動解決が必要になる
   - 解決後、次を実行
     ```bash
     git add <file>
     git commit
     ```

## git reset

```bash
# コミットをステージ後まで戻す
git reset --soft <commit>

# コミットをステージ前まで戻す（デフォルト）
git reset --mixed <commit>

# コミット編集内容まで完全に取り消す
git reset --hard <commit>
```

#### `<commit>`

戻したいコミットを指定する
- `abc1234`：特定のハッシュ値へ戻す
- `HEAD~1`：1つ前のコミットへ戻す

## git restore

作業ツリーやステージに加えた変更を取り消すコマンド　　
ファイルを元の状態に戻すために使う

```bash
# 作業ツリー上の変更を取り消して、最後のコミット時点に戻す
git restore <file>

# ステージに追加した変更をステージから外す
git restore --staged <file>

# 特定のコミット時点の内容に戻す
git restore --source <commit> <file>

# 作業ツリー（ファイルの中身）だけ戻す
git restore --worktree <file>

# 対話形式で戻す変更を選ぶ
git restore --patch <file>
```

## git fetch

```bash
# 全てのリモートの最新情報を取得
git fetch

# 特定のリモートからのみ取得
git fetch <remote>

# 特定のブランチだけ取得
git fetch <remote> <branch>

# リモートで削除されたブランチをローカルでも削除
git fetch --prune

# 登録されている全てのリモートから取得
git fetch --all

# 実際には何もせず、どんな更新があるかだけ確認
git fetch --dry-run
```

# git pull

```bash
# 現在のブランチが追跡しているリモートブランチを自動的にpull
git pull

# 指定したリモートとブランチをpull
git pull <remote> <branch>

# マージではなく、リベースで統合（履歴を直線に保つ）
git pull --rebase

# リベースを使わず、マージで統合
git pull --no-rebase

# Fast-fowardできる場合のみ更新（競合がある場合は中止）
git pull --ff-only

# 処理の詳細を表示
git pull --verbose
```

## git push

```bash
# 現在のブランチを、設定された追跡先リモートにpush
git push

# 指定したリモートとブランチにpush
git push <remote> <branch>

# ローカルブランチとリモートブランチを紐付け
git push -u <remote> <branch>
git push --set-upstream <remote> <branch>

# 強制的にリモートを上書き
git push --force [<remote>] [<branch>]
git push -f [<remote>] [<branch>]

# 自分の変更だけ上書き
git push --force-with-lease [<remote>] [<branch>]

# リモートブランチを削除
git push -delete <remote> <branch>

# タグをまとめてpush
git push --tags

# 全てのブランチをpush
git push --all
```