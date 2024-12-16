# NICの冗長構成(NICチーミング)

## NICチーミングとは

物理NICをまとめて1つの仮想NICとして動作する、Switchは物理NIC分必要

## NICチーミングの種類

### フォールトトレランス

1つの物理NICをActive,それ以外をstandby状態とし、障害が発生したらフォールオーバーして切り替える
※ switchより先で障害が発生した場合、検知できないため通信に不具合が生じる
   回避するためには、リンクステートトラッキング機能を持ったSwitchが必要

### Loadbalancing

トラフィック分散として使用する物理NICを適宜切り替える
※ switchより先で障害が発生した場合、検知できないため通信に不具合が生じる
   回避するためには、リンクステートトラッキング機能を持ったSwitchが必要

### LinkAggregate

チーミングした物理NICをすべて使用して通信帯域を広げる
※ スタック技術に対応しているSwitchが必要

## MultiPathTCP(MPTCP)との違い

- NICチーミング: L2-3層
- MPTCP: L4層、TCPの拡張プロトコル

参考: <https://www.infraexpert.com/study/etherchannel1.html>
