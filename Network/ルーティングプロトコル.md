# ルーティングプロトコルについて

## ルーティング優先度

- 直接ルーティング
- 間接ルーティング
  - 静的ルーティング
  - 動的ルーティング
    - IGP(Interior Gateway Protocol)
      - RIP(Routing Information Protocol)
      - OSPF(Open Shortest Path First)
    - EGP(Exterior Gateway Protocol) ※ 総称として
      - BGP(Border Gateway Protocol)
        - iBGP(Internal BGP)
        - eBGP(External BGP)
      - EGP ※ 単体のルーティングプロトコルとして

## 動的ルーティングプロトコル

- IGP（Interior Gateway Protocol）:ASの内部ルーティングに使用
  - RIP（Routing Information Protocol）
    - ルータのホップ数
  - OSPF
    - 帯域幅
  - IS-IS
- EGP（Exterior Gateway Protocol）:AS間でのルーティングに使用
  - BGP
    - iBGP:同じAS間のピア
    - eBGP:異なるAS間でのピア
  - EGP(狭義の意味)

参考: <https://atmarkit.itmedia.co.jp/ait/articles/0111/06/news002.html>
