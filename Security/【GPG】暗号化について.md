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
