# 【Git】Windows環境で改行コードが勝手に変わる現象について

## 内容

インストール時の設定により、チェックアウト時やコミット時に改行コードが勝手に変わってしまう

## 対処方法

以下のコマンドで設定を変更できる

`git config --global core.autocrlf ${value}`

${value}|チェックアウト時|コミット時
-|-|-
true|LF ⇒ CRLF|CRLF ⇒ LF
input|変換しない|CRLF ⇒ LF
false|変換しない|変換しない
