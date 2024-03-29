## ホストオンリーアダプター

### 概要

```plain
ホストOSとゲストOS,ゲストOS同士で接続できる
ホストOSより先のネットワークとは干渉しないため外部からは見えない
外部に接続しない場合はこれでいい
```

### 接続関係

```plain
ゲストOS ←→ ホストOS
ゲストOS ←→ 他ゲストOS
ゲストOS xx ホストOSが接続しているネットワーク
```

----------------------------------------------

## 内部ネットワーク

## 概要

ゲストOS間のみ接続可能

### 接続関係

```plain
ゲストOS xx ホストOS
ゲストOS ←→ 他ゲストOS
ゲストOS xx ホストOSが接続しているネットワーク
```

## NAT

### 概要

```plain
ホストOSやその先のネットワークに接続できる
しかし、ゲストOS間を含めたゲストOS以外は接続できない(ゲストOSごとに仮想的なルータがあるイメージ)
なんかポートフォワーディングすると接続できる箇所が増えるらしいが省略
```

### 接続関係

```plain
ゲストOS x→ ホストOS
ゲストOS xx 他ゲストOS
ゲストOS x→ ホストOSが接続しているネットワーク
```

----------------------------------------------

### NAT Netwark

### 概要

```plain
NATのゲスト間が接続できる様になったもの
ゲストOS間は同じネットワークでその先に仮想的なルータがあるイメージ
```

### 接続関係

```plain
ゲストOS x→ ホストOS
ゲストOS ←→ 他ゲストOS
ゲストOS x→ ホストOSが接続しているネットワーク
```

----------------------------------------------

## ブリッジアダプタ

### 概要

ゲストOSからもそれ以外からも接続可能

### 接続関係

```plain
ゲストOS ←→ ホストOS
ゲストOS ←→ 他ゲストOS
ゲストOS ←→ ホストOSが接続しているネットワーク
```
