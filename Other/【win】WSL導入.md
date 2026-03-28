# WSL導入

WindowsでGUI触るのあまり好きじゃないのでコマンドでやりたいとか、git bashでできないことをしたいとか

## Process

1. 管理者権限でPowerShellを起動し、以下コマンドを実行
   ```ps
   wsl --install
   wsl --list --oneline
   ```
1. OS再起動
1. 管理者権限でPowerShellを起動し、以下コマンドを実行
   ```ps
   wsl --install -d OracleLinux_9_5
   ```
1. OS再起動
