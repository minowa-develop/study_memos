# rootディレクトリのサイズ拡張(ストレージデバイス拡張)

```bash
#!/bin/bash

ADD_DEV=/dev/sdb
TARGET_VG=almalimux
TARGET_LV=root

# pre status
lsblk
df -Th

# main work
pvcreate ${ADD_DEV}
vgextended ${TARGET_VG} ${ADD_DEV}
lvresize -l100%vg "/dev/${TARGET_VG}/${TARGET_LV}"
xfs_growfs "/dev/${TARGET_VG}/${TARGET_LV}"

# post status
lsblk
df -Th
```
