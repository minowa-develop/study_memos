# ログインシェル変更方法

例としてzshに変更するシェル

```bash
#!/bin/bash

# 使用可能シェル
cat /etc/shells

# ユーザごとのログインシェル確認
cat /etc/passwd | grep ^root

# ログイン中のシェル
echo $SHELL

# シェルインストール
dnf install zsh

# ログインシェル変更
chsh -s /bin/zsh

# 他ユーザの場合
usermod -s /bin/zsh username
```
