# パーティション作成方法

## パーティション作成からマウントまでの流れ

```bash
# パーティション作成 対話コマンドについては後述
fdisk /dev/sdb

# パーティション更新
partprobe

# ファイルシステム作成
mkfs -t ext4 /dev/sdb

# マウント
mkdir /mnt/disk2
mount /dev/sdb /mnt/disk2
```

## fdisk対話コマンド

### 基本形

command|desc
-|-
o|MBRパーティションテーブル作成
g|GPTパーティションテーブル作成
n|パーティション作成
d|パーティション削除
p|状態表示
F|空き状態表示
w|書き込み
q|取り消し

## 論理ボリューム(LVM)作成

```bash
# 物理ボリューム作成(pv:Physical Volume)
pvcreate /dev/sdb1
pvdisplay

# ボリュームグループ作成(vg:Volume Group)
vgcreate volume-grp /dev/sdb1
vgdisplay

# 論理ボリューム作成(lv:Logical Volume)
lvcreate --name public --size 128MB volume-grp
lvdisplay

# ファイルシステム作成とマウント(パーティション作成と同様)
mkfs -t ext4 /dev/mapper/lvg--share-public
mount /dev/mapper/lvg--share-public /mnt/test

# 自動マウント
echo "/dev/mapper/lvg--share-public /mnt/test   ext4    defaults    0 0" >> /etc/fstab
```

### 各リレーション

パーティション 1-1 物理ボリューム 1*-1 ボリュームグループ 1-1* 論理ボリューム
