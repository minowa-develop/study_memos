# Samba(Windows共有)サーバ構築

```bash
#!/bin/bash

# constant
SHARE_PATH="/smb_share/"
USER="smb_test"
GROUP="samba_share"

# user create
useradd "${USER}"
pdbedit -a "${USER}"

# group create and setting
groupadd "${GROUP}"
gpasswd -a "${USER}" "${GROUP}"

# share path create
install -m 775 -g "${GROUP}" -d "${SHARE_PATH}"

# SELinux setting
setsebool -P samba_enable_home_dirs 1
chcon -P -t samba_share_t "${SHARE_PATH}"

# firewall
firewall-cmd --add-service=samba --permanent

# service
systemctl enable smb
systemctl start smb
```

## 設定ファイルに共有ディレクトリ追加

vi /etc/samba/smb.conf

```plain
[share]
        path = "${SHARE_PATH}"
        comment = Samba Directories
        writable = no
        write list = @"${GROUP}"
        force group = "${GROUP}"
        create mask = 765
        directory mask = 775
```
