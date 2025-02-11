# NTFSのディスクイメージをマウントする方法

前提としてntfsをマウントするためにntfs-3gをインストールする必要がある。(from EPEL repository)

```bash
#!/bin/bash

# const
readonly DISK_IMG="unlock.img"
readonly MNT_PATH="testmnt"

# ntfs-3gインストール(ntfsをマウントするため)
dnf install -y ntfs-3g

# ループバックデバイス設定
losetup -f $DISK_IMG

# パーティション設定
partx -a /dev/loop0

# マウント
mount /dev/loop0p2 $MNT_PATH -t ntfs-3g

# デバイス確認
lsblk

# アンマウント
umount $MNT_PATH

# パーティション解除
partx -d /dev/loop*

# ループバックデバイス解除
losetup -d /dev/loop*
```