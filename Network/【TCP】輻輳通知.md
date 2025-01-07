# 輻輳通知

## 流れ

1. send(送信ホスト): ip.ect=1
1. 輻輳発生(NW/HW): ip.ect==1?ip.ce=1
1. receive(受信ホスト): ip.ce==1?is輻輳
1. response(受信ホスト): tcp.ece=1
1. resend(送信ホスト): tcp.cwr=1

## IPヘッダ

- ECN(Explicit Congestion Notification:明示的輻輳通知)
  - 1ビット: ECT(ECNCapable Transport)
    - 上位層のトランスポートプロトコルがECNに対応しているか
    - 0: 非対応、1: 対応
  - 2ビット: CE(Congestion Experienced)
    - 輻輳しているかどうか
    - 0: 通常、1: 輻輳

## TCPヘッダ

- ECE
- CWR
