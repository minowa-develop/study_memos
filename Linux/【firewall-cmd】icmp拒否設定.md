#　ICMPのブロック

firewall-cmdでの説明となる

## icmp-block-inversion

ホワイトベースで拒否状態にする

- no(default): ブラックリスト`--add-icmp-block-inversion`
- yes: ホワイトリスト`--remove-icmp-block-inversion`

## icmp-block

icmpのタイプを指定してブロック or 許可状態にする

- 追加: `--add-icmp-block=ICMPのタイプ`
- 削除: `--remove-icmp-block=ICMPのタイプ`

## ICMPのタイプ一覧

`--get-icmptypes`

## Examples

### echo-requestのみ拒否する場合

```bash
#!/bin/bash

firewall-cmd --remove-icmp-block-inversion # 基本許可
firewall-cmd --add-icmp-block=echo-request # 判定指定(許可->拒否)
```

### echo-requestのみ許可

```bash
#!/bin/bash

firewall-cmd --add-icmp-block-inversion # 基本拒否
firewall-cmd --add-icmp-block=echo-request # 判定指定(拒否->許可)
```
