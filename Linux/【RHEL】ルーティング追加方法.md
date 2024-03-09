# ルーティング追加方法

## 対象ファイル

/etc/networkmanager/system-connections/${対象のコネクション}.nmconnection

## 追加

`route1=${IN_CIDR}, ${GW_ADDR}`
