# KDE Plasmaインストール方法

`dnf -y group install "KDE Plasma Workspaces"`
`dnf -y group install "KDE Plasma Workspaces" "base-x"`

AlmaLinuxの場合は、crbリポジトリを有効にする必要がある

```bash
#!/bin/bash

dnf config-manager --set-enabled crb
```

参考: <https://www.server-world.info/query?os=Fedora_38&p=desktop&f=2>
参考: <https://medium.com/@manikandanprakash.p/install-kde-desktop-on-centos-9-almalinux-9-rhel-9-09bc12045862>
