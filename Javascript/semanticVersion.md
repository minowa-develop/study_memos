# Semantic Version

x.y.z表記のバージョン

## バージョン指定方法(npm)

種類|基本|例外
-|-|-
~x.y.z(チルダ range)|表記されている箇所は固定|パッチバージョンまで指定されていたら、メジャー、マイナーのみ固定となる
^x.y.z(キャレッジ range)|先頭のバージョンのみ固定|先頭のバージョンは0だった場合は先頭をずらす
