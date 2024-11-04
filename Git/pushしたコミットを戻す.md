# 誤ってpushしたコミットを取り消す

## resetを使用する方法

特徴として、戻すコミット以降のコミット(誤ったコミット)はなかったことになる

```bash
git reset --hard ${commit-id}
git push -f
```

参考: <https://qiita.com/S42100254h/items/db435c98c2fc9d4a68c2>
