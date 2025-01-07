# DHCPのやり取り

no|Client|send|DHCP|宛先|desc
:-:|-|:-:|-|-|-
1|discover|->||broadcast|要求
2||<-|offer|unicast|IPアドレス提示
3|request|->||broadcast or unicast(※1)|IPアドレス提示
4||<-|ack or nak(※2)|unicast|requestに対する結果

※1: 初回: broadcast, 更新: unicast
※2: 初回はack固定

## パターン

初回: 1-4
更新: 3-4(更新でnakの場合は初回の手順を行う)
