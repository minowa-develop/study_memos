# 【RHEL】ユーザのグループやら権限系のコマンドまとめ

## 簡単に

- グループ自体の作成削除: `group{add,del} $group`
- グループにユーザの追加除外: `gpasswd -{a,d} $user $group`
- 所属グループ: `groups $user`
- 所属ユーザ: `getent group $group`

## グループ操作系

cmd|desc
-|-
groupadd ${GROUP}|グループ作成
groupdel ${GROUP}|グループ削除
gpasswd -a ${USER} ${GROUP}|ユーザにグループを追加
gpasswd -d ${USER} ${GROUP}|ユーザのグループを削除
groups ${USER}|ユーザが所属しているgroupを表示
getent group ${GROUP}|グループに所属するユーザを表示
cat /etc/group|グループ確認

## ファイル権限操作系

cmd|desc
-|-
chmod ${NO} ${PATH}|ファイルの権限変更 no:所有者,所有グループ,その他
`chown ${USER}[${:GROUP}] ${PATH}`|ファイルの所有者,グループ変更
