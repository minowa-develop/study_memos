# ロケール変更関係

## 現状のロケール確認
```plain
$ localectl status
   System Locale: LANG=en_US.UTF-8
       VC Keymap: jp
      X11 Layout: jp
```

## ロケール変更

`localectl set-locale LANG=ja_JP.utf8`

## ロケール変更後の確認

`less /etc/locale.conf`

## 反映
`source /etc/locale.conf`

lsやviの文字が日本語になったりするかも