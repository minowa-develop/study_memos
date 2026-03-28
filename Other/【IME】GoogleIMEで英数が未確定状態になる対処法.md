# GoogleIMEで半角英数が日本語のように未確定状態になってしまう解決方法

## Process

1. プロパティからキー設定のキー設定の選択をカスタムにして編集
1. エントリーがアレばすべて削除(編集からエントリを削除できる) 
1. 編集から定義済みのキーマップからインポートを選び、土台となるものを選択する
1. 以下を編集/追加する(入力キーでソートしたほうが見やすい)
   モード|入力キー|コマンド
   -|-|-
   直接入力|Eisu|ひらがなに入力切り替え
   入力文字なし|Eisu|IMEを無効化
   変換前入力中|Eisu|IMEを無効化
   変換中|Eisu|IMEを無効化

## Eisuが入力できない場合

編集からエクスポートして、そのファイルに以下を変更/追加しインポートする

```plain
DirectInput	Eisu	CompositionModeHiragana
Precomposition	Eisu	IMEOff
Composition	Eisu	IMEOff
Conversion	Eisu	IMEOff
```

## Memo

おそらく、英数入力時は直接入力(おそらくIME無効化状態)がよい

直接入力(英数入力)時に切り替えた場合はひらがなに、それ以外はIME無効化(英数入力)にする感じ？

IME無効化 = 直接入力 = 英数入力？

