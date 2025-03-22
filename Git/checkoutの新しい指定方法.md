# 個人的によく使うgit checkoutコマンドの新規コマンドへの置き換え

- ブランチ切り替え
  `git checkout ${BRANCH}` -> `git switch ${BRANCH}`
- リモートブランチをローカルに取り込む
  `git checkout -b ${LOCAL_BRANCH} origin/${REMOTE_BRANCH}` -> `git switch -c ${LOCAL_BRANCH} origin/${REMOTE_BRANCH}`
- コミット切り替え(detached状態)
  `git checkout ${COMMIT_ID}` -> `git restore ${COMMIT_ID} --detach`
- ファイルの変更を取り消す
  `git checkout ${FILE}` -> `git restore ${FILE}`
- 全てのファイルの変更を取り消す
  `git checkout -- .` -> `git restore -- .`
- 特定のコミットのファイルを戻す
  `git checkout ${COMMIT_ID} ${FILE}` -> `git restore -s ${COMMIT_ID} ${FILE}`

参考: <https://zenn.dev/gmomedia/articles/d9366fa84aadfd>
