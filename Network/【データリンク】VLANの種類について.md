# 【ネットワーク】VLANの種類について

## VLANとは

レイヤ2スイッチでネットワークを分割するための技術

## VLANの種類

種類|desc
-|-
ポートVLAN(一般的)|スイッチングハブの**ポート**（差込口）単位でVLANの割り当てを行う方法
タグVLAN|ネットワークを流れる個々の**データのフレーム**に、転送先のグループの識別番号を付与する方法
MACベースVLAN|**MACアドレス**をもとにして、ネットワークごとに割り振りする
ユーザーベースVLAN|ネットワークを使う**ユーザの認証情報**によって識別する方法
サブネットベースVLAN|**IPアドレス**によって識別する方法
