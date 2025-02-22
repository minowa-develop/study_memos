# WAN環境のL2プロトコル

- PPPoE, IPoE: WAN上のデータリンク層(L2)
- MAP-E, IPIP: IPv6 over IPv4技術
- IPv4, IPv6: ネットワーク層(L3)

- PPPoE(PPP over Ethernet): ユーザ名とパスワードで認証する方法、ヘッダーが大きい
- PPPoA(PPP over ATM): ATMにPPPの認証機能を付与したもの、古いADSLで使用される
- IPoE(IP over Ethernet): ユーザ認証なし、ヘッダーが小さい
- PPP(Point to Point Protocol): PAPやCHAPを利用してユーザ認証を行うプロトコル、ダイヤルアップやDSL(ADSL)などで利用される

※ WAN上のL2プロトコルと言ったらIPoEやPPPoEを指す、普通のEthernetは使用されない

L3|L2|L1
-|-|-
ダイヤルアップ|PPP|アナログ電話回線
IDSN|Dチャネル、Bチャネル|ディジタル電話回線
ADSL|PPP,ATM|アナログ電話回線
