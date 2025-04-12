# sudoコマンド

sudoを付ければ実行できるようにするにはsudoersファイル or wheelにユーザを追加する必要がある

※ rootはスーパーユーザなため、sudoを付けなくても全てのコマンドが使用できる

## sudoログ有効方法

`echo "Defaults logfile=/var/log/sudo.log" > /etc/sudoers.d/sudolog`
