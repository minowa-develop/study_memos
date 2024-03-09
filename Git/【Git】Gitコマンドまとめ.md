# Gitコマンドまとめ

## 初期化

### cloneの方法

- `git clone "${URL}"`
- `git clone "${URL}" "${LOCAL_DIR}"`

### 既存のディレクトリを使用する方法

1. `git init`
1. `git remote add origin "${URL}"`
1. `git fetch`

## ブランチ変更

### ブランチ一覧

`git branch -a`

### ブランチ作成

`git branch ${BRANCH}`

### リモートブランチを元にして作成

1. `git checkout -b "${NEW_BRANCH}" "origin/${SRC_BRANCH}"`
1. `git push -u origin "${BRANCH}"`

### ブランチ移動

`git checkout ${BRANCH}`

## ブランチ削除

1. `git branch -d "${BRANCH}"`
2. `git push origin -d "${BRANCH}"`

## pull

- `git pull`
- `git pull origin "${URL}"`

## pushまでの流れ

### 変更済みファイル一覧

`git status`

### ステージング:追加

- `git add "${FILE}"`
- `git add *`

### ステージング:削除

- `git reset "${FILE}"`
- `git reset *`

### 変更済みのファイルをもとに戻す

`git checkout "${FILE}"`

### commit

`git commit -m "${MESSAGE}"`

### push

- `git push`
- `git push origin "${BRANCH}"`

## ブランチマージ

1. `git merge ${BRANCH}`
1. `git push`

### コンフリクト解決方法

1. テキストエディタなどで修正
1. pushのcommit以降を実行

----------------------------------

## その他

### リモートリポジトリと紐づける

1. `git branch -vv`
1. `git branch -u "origin/${BRANCH}"`

### ブランチ作成のながれ

1. `git checkout -b "${BRANCH}" origin/{SRC_BRANCH};git push -u origin "${BRANCH}"`
2. `git add *;git commit "${MESSAGE}";git push`
