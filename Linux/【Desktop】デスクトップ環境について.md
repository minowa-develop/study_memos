# Linux デスクトップ環境

## 起動順序

XserverとWindow Managerは並列起動される

1. BIOS(H/W)
1. GRUB(BootLoader)
1. systemd
1. Display Manager
1. Xserver
   - x.org
   - wayland
1. Window Manager
   - mutter(waylandコンポジタ)
   - metacity

waylandコンポジタはXserver(wayland)の機能も一部持っている
