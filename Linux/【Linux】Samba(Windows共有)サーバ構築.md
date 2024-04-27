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

## sambaリソースをマウントする

```bash
#!/bin/bash

# constant
SAMBA_HOST="192.168.0.65"

# 共有ディレクトリ
SAMBA_PATH="smb_share"
MOUNT_PATH="/mnt/smb_share/"
mkdir "${MOUNT_PATH}"
mount -t cifs "//${SAMBA_HOST}/${SAMBA_PATH}" "${MOUNT_PATH}"

# user home
MOUNT_PATH="/mnt/smb_home/"
USER="smb_test"
SAMBA_PATH=$USER
PASS="test"
mkdir "${MOUNT_PATH}"
mount -t cifs -o "username=${USER},password=${PASS}" "//${SAMBA_HOST}/${USER}" "${MOUNT_PATH}"
```
