# Samba(Windows共有)サーバ構築

```bash
#!/bin/bash

# Linuxユーザ作成
useradd smb_user
passwd smb_user

# LinuxユーザをSambaアクセスユーザとして作成
pdbedit -a smb_user

# 共有ディレクトリ作成
mkdir /tmp/smb_public
chown nobody: /tmp/smb_public

# SMB設定変更
sed -iE "s/workgroup = .*/workgroup = WORKGROUP/" /etc/samba/smb.conf

# firewall
firewall-cmd --add-service=samba --parmanent

# SELinux設定 (セキュリティ的に良くないかも)
setsebool -P samba_export_all_ro=1 samba_export_all_rw=1
```

## SELinux設定項目

### samba_export_all_ro

```plain
あらゆるファイルやディレクトリをエクスポートし、 読み取り専用のパーミッションを付与します。
これにより、 samba_share_t タイプのラベルが付いていないファイルやディレクトリを Samba で共有できるようにします。
samba_export_all_ro Boolean はオンになっているが、 samba_export_all_rw Boolean がオフになっている場合、 /etc/samba/smb.conf で書き込みアクセスが設定され Linux パーミッションでも書き込みアクセスが許可されていても、 Samba 共有への書き込みアクセスは拒否されます。
```

### samba_export_all_rw

```plain
あらゆるファイルやディレクトリをエクスポートし、 読み取りと書き込みのパーミッションを付与します。
これにより、 samba_share_t タイプのラベルが付いていないファイルやディレクトリを Samba でエクスポートできるようにします。
/etc/samba/smb.conf のパーミッションおよび Linux パーミッションを設定して書き込みアクセスを許可する必要があります。
```
