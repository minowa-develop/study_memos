# KDE Plasmaインストール方法

`dnf -y group install "KDE Plasma Workspaces"`

AlmaLinuxの場合は、crbリポジトリを有効にする必要がある

```bash
#!/bin/bash

dnf config-manager  --set-enabled crb
```

参考: <https://www.server-world.info/query?os=Fedora_38&p=desktop&f=2>
