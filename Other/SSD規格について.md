# SSD規格

## 接続規格

- SATA(Serial ATA)
  HDDや光学ドライブなどで普及している接続規格、データと電源の2本つながないといけない
- PCIe(Peripheral Component Interconnect-Express)
  グラボとかサウンドボードとかキャプチャボードとかいろいろ拡張できる

## 通信プロトコル

- AHCI
  HDD用として設計された
- NVMe(Non-Volatile Express)
  フラッシュメモリを効率よくした通信プロトコル

## 組み合わせ例

接続規格|通信プロトコル|補助記憶装置|用途
-|-|-|-
SATA|AHCI|HDD|一般的なHDD接続
SATA|AHCI|SSD|SATA SSD
PCIe|MVNe|SSD|M.2 SSD
