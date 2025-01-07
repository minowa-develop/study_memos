# LVM RAID1構築

## RAID1構築

```bash
# RAID1対象のHDD2台のPV作成
pvcreate /dev/sdb /dev/sdc

# HDD2台をVGにまとめる
vgcreate raid_grp /dev/sdb /dev/sdc

# RAID1のLVを作成
lvcreate -n raid_lvm --type raid1 -m1 -l100%FREE raid_grp
```

## HDD片方破損時の対応方法

```bash
# ディスク破壊(HDD破損再現)
dd if=/dev/urandom of=/dev/sdb
shred /dev/sdb

# 論理ボリュームをアクティブ化(yをnにすると無効化)
lvchange -ay raid_grp/raid_lvm

# 新しいHDDでPV作成
pvcreate /dev/sdb

# 新しいPVをグループに含める
vgextend raid_grp /dev/sdb

# 修復
lvconvert --repair raid_grp/raid_lvm

# 破損したpvをvgから削除
vgreduce --removemissing --force raid_grp
```

## LV構造変更

### HDD1台からミラーリングに変更

```bash
# HDD1台構成
pvcreate /dev/sdb
vgcreate raid_grp /dev/sdb
lvcreate -n raid_lvm -l100%FREE raid_grp

# PVS追加
pvcreate /dev/sdc
vgextend raid_grp /dev/sdc

# ミラーリング対応
lvresize -l49%vg raid_grp/raid_lvm
lvconvert -m1 raid_grp/raid_lvm
lvresize -l100%PVS raid_grp/raid_lvm
```

### ミラーリングからHDD1台構成に変更

`lvconvert -m0 raid_grp/raid_lvm /dev/sdb`
