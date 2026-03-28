# GPG使用方法

説明|option
-|-
主鍵ペア作成|--gen-key
サブキー作成|--edit-key ${mailaddress}
鍵削除|--delete-keys ${mailaddress}
pubkey一覧|-k
prikey一覧|-K
ASCII形式|-a
暗号化|-e ${file}
暗号化公開鍵指定|-r ${mailaddress}
出力ファイル名|-o ${outputfile}
復号化|gpg ${file}.{gpg,asc}
署名作成(圧縮)|-s ${file}
署名作成(非圧縮)|--clearsign ${file}
署名作成(別ファイル)|-b ${file}
検証|--verify ${file}.{sig,asc}
検証(別ファイル)|--verify ${file}.{sig,asc} ${file}

## 参考

- <https://yu8mada.com/2018/04/03/how-to-encrypt-decrypt-sign-and-or-verify-files-in-gpg/>
- <https://yossi-note.com/basic_knowledge_of_gpg/#toc5>

## memo(後でマージする)

## 初期設定

command|desc
-|-
dnf install pinentry -y|鍵作成に必要なパッケージ

## 鍵操作

command|desc
-|-
gpg --full-generate-key|鍵ペア(主鍵)作成
gpg --delete-key KEY-ID|公開鍵削除
gpg --delete-secret-keys KEY-ID|秘密鍵削除

## 暗号化

command|desc
-|-
gpg --symmetric secret.txt|対称鍵暗号
gpg --encrypt --recipient KEY-ID secret.txt|公開鍵暗号
gpg --encrypt --armor --recipient KEY-ID secret.txt|公開鍵暗号(ASCII形式)
gpg --decrypt secret.txt.gpg|復号
