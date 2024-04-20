# 【Linux】パーティション形式(GPT,MBR),ファイルシステム確認方法

## パーティション形式

パーティション形式|BIOS(広義的な意味)|コマンド
-|-
MBR(Master Boot Record)|BIOS(Basic Input Output System)|fdisk
GPT(GUID Partition Table)|UEFI(Unified Extensible Firmware Interface)|parted

### 確認方法

1. `parted -l|grep Partition Table`
1. msdos:MBR gpt:gpt

## ファイルシステム

- `df -T`
- `lsblk -f`

## パーティション

- `fdisc -l`
