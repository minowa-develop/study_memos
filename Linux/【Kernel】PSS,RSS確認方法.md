# Rss確認方法

## 確認方法

3通りある

名称|command
-|-
psコマンド|`ps u -p${pid} \| awk '{sum += $6}END{print sum}'`
smapsファイル|`awk '/^Rss/{sum+=$2}END{print sum}' /proc/${pid}/smaps`
pmapコマンド|`pmap ${pid} -x \| tail -1 \| awk '{print $4}'`

## 検証

```bash
#!/bin/bash
pid=1081

ps u -p${pid} | awk '{sum += $6}END{print sum " for ps"}' &
awk '/^Rss/{sum+=$2}END{print sum " for smap"}' /proc/${pid}/smaps &
pmap ${pid} -x | tail -1 | awk '{print $4 " for pmap"}' &
```

## 結果

smapファイルとpmapコマンドの結果は同じ、psだけ異なる結果を出力した
参考: <https://qiita.com/white_aspara25/items/cfc835006ae356189df3>

```plain
417528 for smap
412572 for ps
417528 for pmap
```

## 余談:Pssの出力方法

```bash
#!/bin/bash
pid=1081

awk '/^Rss/{sum+=$2}END{print sum " for smap"}' /proc/${pid}/smaps
```
