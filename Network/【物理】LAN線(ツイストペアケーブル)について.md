# LAN線(ツイストペアケーブル)について

前提として、ツイストケーブルは信号線が2本1組で4対8心のケーブルである

## ケーブルの種類

広義種類|ISO/IEC 11801|全体|ペア線
-|-|-|-
UTP|U/UTP|false|false
STP|U/FTP|false|true
STP|F/UTP|true(ホイル)|false
STP|F/FTP|true(ホイル)|true
STP|S/UTP|true(網)|false
STP|S/FTP|true(網)|true

※ FTPケーブルはアース処理が必要

## ISO/IEC 11801命名規則

### 表記

`x`/`y`TP

- `x`: 全体シールドの種類
- `y`: ペア線シールドの種類

### シールドの種類

表記|desc
-|-
U|シールドなし
F|フォイルシールド(ホイル)
S|編組シールド(網)

## ノイズについて

種類|desc
-|-
クロストーク|ペア線同士でノイズ干渉する
エイリアンクロストーク|LAN線同士でノイズ干渉する

## ペア線の構造

構造|ノイズ耐性|柔軟性|本数
-|-|-|-
より線|弱い|やわらかい|複数
単線|強い|かたい|1本

参考: [https://e431.jp/shop/pages/basics_LAN.aspx]
