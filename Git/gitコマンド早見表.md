# gitコマンド早見表

## 初期系

command|desc
-|-
git clone ${ssh-url}|リモートリポジトリからクローンする
git init|既存のディレクトリをgit化
git remote add origin ${ssh-url}|既存のディレクトリとリモートリポジトリを紐付ける

## ブランチ系

command|desc
-|-
git branch -vv|ローカルブランチとリモートブランチの紐付け状態表示
git branch -a|ローカルブランチとリモートブランチ一覧表示
git branch ${local-branch}|ローカルブランチを作成
git branch -d ${local-branch}|ローカルブランチ削除
git branch -u origin/${remote-branch}|リモートブランチを紐付け

## ローカル操作系

command|desc
-|-
git checkout ${local-branch}|ローカルブランチに切り替える
git checkout -b ${local-branch} ${source-branch}|sourceブランチを元にローカルブランチを作成
git checkout ${file}|ファイルを変更前に戻す

## リモート操作系

command|desc
-|-
git push|コミットした内容をリモートブランチに反映
git push -d origin ${remote-branch}|リモートブランチを削除
git push -u origin ${local-branch}|ローカルブランチを元にリモートブランチを作成

## ログ系

command|desc
-|-
git log --graph|ログをグラフィカルに表示
git log ${branch}|対象のブランチのログを表示

## diff系

command|desc
-|-
git diff|現在と最新コミットで比較(ステージング前)
git diff --cached|ステージング後と最新コミットで比較(ステージング後)
git diff HEAD^|最新コミットと前回のコミットで比較(コミット後)
git diff ${branch1}..${branch2}|ブランチ同士で比較
git diff --text|上記の内容で強制的にテキストとして表示

## stash系

command|desc
-|-
git stash|変更した内容をスタッシュに隠す
git stash pop|スタッシュに隠した内容を戻す
git stash drop|直近のスタッシュを削除する

## ステージング系

command|desc
-|-
git add ${file}|ステージング
git reset ${file}|ステージングから外す
