# 【一般知識】gitコマンド

## clone

`git clone ${URL} ${LOCAL_PATH}`

----------------------------------

## 既存のdirにrepositoryをセット

`git remort add origin ${URL}`

----------------------------------

## レポジトリのブランチを紐づける

### 確認

`git branch -vv`

### 設定

`git branch -u origin/${BRANCH}`

----------------------------------

## branch

### branch list by localrepository only

`git branch`

### branch all list

`git branch -a`

### create branch

`git branch ${branch}`

### change branch

`git checkout ${branch}`

----------------------------------

## pull

### pull

`git pull origin ${BRANCH}`

### fetch

`git fetch`

### marge

`git merge`

----------------------------------

## commit

### starging add

`git add ${filename}`

### starging del

`git reset ${filename}`

### commit

`git commit -m "${comment}"`

----------------------------------

## push

`git push origin ${branch}`
