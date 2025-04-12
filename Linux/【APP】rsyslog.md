# rsyslog

Linuxでsyslog送信するデーモンである

## Facility

ログメッセージの種類をあらわす

ファシリティ|ファシリティコード|説明
-|-|-
kern|0|カーネルメッセージ
user|1|ユーザーレベルメッセージ
mail|2|メールシステム
daemon|3|システムデーモン
auth|4|セキュリティ/認証メッセージ(最近のシステムでは、authprivが使用される)
syslog|5|syslogdによる内部メッセージ
lpr|6|Line Printerサブシステム
news|7|newsサブシステム
uucp|8|UUCPサブシステム
cron|9|cronデーモン
authpriv|10|セキュリティ/認証メッセージ(プライベート)
ftp|11|ftpデーモン
local0~local7|16~23|ローカル用に予約

参考: [\[メモ\]Linux syslog ファシリティ・プライオリティ一覧](https://qiita.com/alpha_z/items/b22e0b8ee6a62989cf06)

## Priority

ログレベルを表す

プライオリティ|説明
-|-
emerg|emergency:パニックの状態でシステムは使用不可
alert|alert:緊急に対処が必要
crit|critical:緊急に対処が必要。alertより緊急度は低い
err|error:エラー発生
warning|warning:警告。対処しないとエラーが発生する可能性がある
notice|notice:通常では無いが、エラーでも無い
info|information:通常の稼働の情報
debug|debug:デバッグ情報
none|none:ログメッセージを記録しない

参考: [\[メモ\]Linux syslog ファシリティ・プライオリティ一覧](https://qiita.com/alpha_z/items/b22e0b8ee6a62989cf06)

## syslog送信設定

参考: <https://www.kagoya.jp/howto/engineer/itsystem/syslog/>

```bash
#!/bin/bash

# const
USE_TCP="@@"
USE_UDP="@"

# manual setting
SYSLOG_SERVER_HOST="syslog-server.example.jp"
SYSLOG_SERVER_PORT=514
USE_PROTOCOL=$USE_TCP
TARGET_LOG_FACILITY="*"
TARGET_LOG_PRIORITY="*"

echo "\"${TARGET_LOG_FACILITY}.${TARGET_LOG_PRIORITY}\" \"${USE_PROTOCOL}${SYSLOG_SERVER_HOST}:${SYSLOG_SERVR_PORT}\"" >> /etc/rsyslog.conf

systemctl restart rsyslog
```

※ syslog-serverのfirewallを開けておくことを忘れずに
