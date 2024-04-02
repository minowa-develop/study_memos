# linuxのファイル参照方法(inode)

example: /home/minowa/hoge.txt

```java
Inode rootInode = "/"
Data rootData = rootInode.getDateBlockNo(); // /のinodeからデータブロック番号を取得して/のデータを取得

Inode homeInode = rootData.getChild("home");　// /のデータからhomeのinodeを取得
Data homeData = homeInode.getDateBlockNo(); // homeのinodeからデータブロック番号を取得してhomeのデータを取得

Inode minowaInode = homeData.getChild("minowa");　// homeのデータからhomeのinodeを取得
Data minowaData = minowaInode.getDateBlockNo(); // minowaのinodeからデータブロック番号を取得してminowaのデータを取得

Inode hoge_txtInode = minowaData.getChild("minowa");　// minowaのデータからhoge.txtのinodeを取得
Data hoge_txtData = hoge_txtInode.getDateBlockNo(); // hoge.txtのinodeからデータブロック番号を取得してhoge.txtのデータを取得
```

参照: [https://qiita.com/KenjiOtsuka/items/1e33b3fa730d6d9dc713]
