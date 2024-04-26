# ルーティング追加方法

## 一時的(再起動やnmcli c uで取り消される)

`route add -net "${IN_CIDR}" gw "${GW_ADDR}"`

## 対象ファイル

/etc/networkmanager/system-connections/${対象のコネクション}.nmconnection

## 追加

`route1=${IN_CIDR}, ${GW_ADDR}`
