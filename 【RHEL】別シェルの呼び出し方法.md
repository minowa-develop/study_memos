# 【RHEL】別シェルの呼び出し方法

## シェルスクリプトの呼び出し方法とその違いについて

### シェルスクリプトの呼びだし方法と挙動の違い

記述|シバン必須|実行権限必須|現在動作しているシェルの影響|特徴
-|-|-|-|-
./hoge.sh|**true**|**true**|false|シバンと実行権限が必須
bash ./hoge.sh|false|**true**|false|実行権限が必須
source ./hoge.sh|false|false|**true**|シェルの影響あり、Ubuntuでは実行できない
. ./hoge.sh|false|false|**true**|sourceと一緒、Ubuntuでも使用可能

### 現在動作しているシェルの影響について

シェル変数やエイリアスが引き継がれる。
