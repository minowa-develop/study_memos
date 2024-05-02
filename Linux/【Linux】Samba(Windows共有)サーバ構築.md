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

## sambaリソースをマウントする(cifs-utils無し)

基本的ににcifs-utilsを入れておいたほうがよい、ドメイン名指定が可能だったり、パスワードをコマンドラインに記載しなくていいので安全、
下記のコマンドはcifs-utils無い場合なのである場合は`,password=${PASS}`を取り除いてください

```bash
#!/bin/bash

# constant
SAMBA_HOST="192.168.0.65"
USER="smb_test"
PASS="test"

# 共有ディレクトリ
SAMBA_PATH="smb_share"
MOUNT_PATH="/mnt/smb_share/"
mkdir "${MOUNT_PATH}"
mount -t cifs -o "username=${USER},password=${PASS}" "//${SAMBA_HOST}/${SAMBA_PATH}" "${MOUNT_PATH}"
```
