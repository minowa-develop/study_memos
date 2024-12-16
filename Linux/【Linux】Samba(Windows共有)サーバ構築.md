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

## cifsの自動マウント方法

cifsutils必須

```bash
#!/bin/bash

# constant(上記のconstantを継承)
CREDENTIALS_FILE=/etc/smb_credentials/.samba

# credentialファイル作成
cat <<< "
username=${USER}
password=${PASS}
" > ${CREDENTIALS_FILE}

# fstab書き込み
echo "//${SAMBA_HOST}/${SAMBA_PATH} ${MOUNT_PATH}      cifs    nofail,_netdev,x-systemd.automount,credentials=${CREDENTIALS_FILE}      0 0" >> /etc/fstab
```

## sambaでファイルにアクセスできない場合

samba自体は構築出来てて該当のディレクトリ、ファイルのみがアクセスできない場合に対応

### DAC権限

chmod -R 774 /smb_share/${targer}
chown -R root:samba /smb_share/${target}

### MAC権限(SELinux)

chcon -r -t samba_share_t /smb_share/${target}

### user group(グループでDACする場合)

grep ${user} /etc/group
