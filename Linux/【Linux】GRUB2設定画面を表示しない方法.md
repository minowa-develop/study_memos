# 【Linux】GRUB2設定画面を表示しない方法

```bash
#!/bin/bash

# 設定変更
sed -iE "s/GRUB_TIMEOUT=5/GRUB_TIMEOUT=0/" /etc/default/grub

# 設定反映
grub2-mkconfig -o /boot/grub2/grub.cfg
```
