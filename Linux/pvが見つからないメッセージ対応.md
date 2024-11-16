# deviceが見つからない旨のメッセージが出た場合

おそらく`/etc/lvm/devices/system.devices`ファイルに記載されているIDNAMEが認識されているストレージのIDと異なるので変更する

```bash
#!/bin/bash

NOT_FOUND_DEVICE=sda

# show pv-uuuid
ll /dev/disk/by-id/ | grep -e "lvm-pv-uuid-.*$NOT_FOUND_DEVICE" | sed -E "s/^.*lvm-pv-uuid-([^ ]+) .*/\1/"

# show IDNAME
ll /dev/disk/by-id/ | grep -e "scsi-0.*$NOT_FOUND_DEVICE" | sed -E "s/^.*scsi-0([^ ]+) .*/\1/"

# show smart(HDD info)
smartctl -a /dev/sda

# modify file
vi /etc/lvm/devices/system.devices
```
