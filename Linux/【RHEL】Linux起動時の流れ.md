Linux起動時の流れ

1. 電源投入
1. BIOS/UEFIの起動
1. ブートローダ（GRUB,GRUB2..）
1. カーネル（vmlinuz）とinitramfs（初期RAMディスク）の読み込み
1. カーネルの実行
1. initramfs（初期RAMディスク）の実行
1. initの実行（SysVinit,Systemd..）

参考: [https://www.konosumi.net/entry/2020/09/27/223948]
