# 【ネットワーク】NetBIOS関係

## NetBIOS(Network Basic Input/Output System)

- Microsoftのネットワーク環境を実現する上位通信プロトコル(tcp/ipでいうアプリケーション層?)
- 下位プロトコルに、IPX/SPXやNetBEUIやTCP/IPが使用される

## NetBEUI(NetBIOS Externded User Interface)

- 昔使用されていた、Microsoftのネットワーク環境(LAN Manager)を実現する下位通信プロトコル
- 現在ではTCP/IPが主流
- NetBIOS名で通信相手の特定を行う(IPは使用しない)

## NBT(NetBIOS over TCP/IP)

- 上位通信プロトコルにNetBIOS、下位通信プロトコルにTCP/IPを使用したもの
  - アプリケーション: NetBIOS
  - トランスポート: TCP/UDP
  - インターネット: IP
  - インターフェース: テキトー

### NBTの使用ポートについて

- 137/udp: 名前解決(NetBIOSからIPアドレスを解決)
- 138/udp: ブラウジング(ネットワークとコンピュータ一覧表示)
- 139/tcp: NetBIOSセッションサービス(ファイルやプリンタ共有)