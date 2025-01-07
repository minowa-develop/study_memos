# sshのログイン許可方法について

## PermitRootLogin: rootユーザでのログインを制限(対象はrootユーザのみ)

Value|Desc
-|-
yes|ログインを許可
no|ログインを禁止
without-password|パスワード認証を禁止(鍵認証は許可)
prohibit-password|without-passwordと同様、RHEL9で使用されている

## PasswordAuthentication: パスワード認証の許可状態

Value|Desc
-|-
yes|パスワード認証を許可
no|パスワード認証を不可
