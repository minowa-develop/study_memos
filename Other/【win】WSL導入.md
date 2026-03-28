# WSL導入

WindowsでGUI触るのあまり好きじゃないのでコマンドでやりたいとか、git bashでできないことをしたいとか

## Install

1. 管理者権限でPowerShellを起動し、以下コマンドを実行
   ```ps
   wsl --install
   wsl --list --oneline
   ```
1. OS再起動
1. Windows storeでAlmaLinuxなど検索してインストールする
   - AlmaLinux10: <https://apps.microsoft.com/detail/9N2VHJMS6J50?hl=neutral&gl=JP&ocid=pdpshare>

## よく使うWSLコマンド

Command|Desc
-|-
wsl -l -v|各OSの状態リスト
wsl --set-default ${NAME}|wslで起動できるデフォルトのOS
wsl -d ${NAME}|OS指定起動
wsl --terminate ${NAME}|OS停止
wsl --shutdown|すべてのOS停止

## WSLの設定

%USERPROFILE%\.wslconfig

```plain
[wsl2]
memory=4GB
processors=2
swap=0
```

## WSLのディレクトリ

%LOCALAPPDATA%\Packages\

## Security

WSLのOSに入る

```bash
sudo cat <<< EOS >> /etc/wsl.conf
[interop]
enabled=false
appendWindowsPath=false
EOS
```

WSLの再起動: `wsl --shutdown`
