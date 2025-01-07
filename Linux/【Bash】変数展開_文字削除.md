# 変数展開_文字削除

## 文字

Char|descript
-|-
\#|前方マッチ
%|後方マッチ

## 個数

Count|Descript
-|-
1|最短マッチ
2|最長マッチ

## Example

`test=192.0.2.0`

Command|Result
-|-
echo ${test#*.}|0.2.0
echo ${test##*.}|0
echo ${test%.*}|192.0.2
echo ${test%%.*}|192
※ 後方マッチで*.や先方マッチで.*は変化しない
