# MD5とは

## 特徴

- 暗号学的ハッシュ関数のひとつである。ハッシュ値は128ビット
- 古くからソフトウェアの配布などで利用者が受け取ったファイルが配布されているものに相違ないかを確かめるのによく利用された
  - 途中でデータの改竄や欠落、破損などが起こっていないか確認が可能
- セキュリティ用途で使用するのは安全ではないため、他のハッシュ関数を使用する

## ハッシュ関数とは

- 元に規則性のない固定長のデータを算出する関数
- 同じ入力値からは必ず同じ値が得られる一方、わずかでも入力値が異なるとまったく違う出力値になる
- 違うデータからも、同じハッシュ値が出る可能性がある、これを「衝突」と呼んでいます。
- 故意に衝突を起こすことでデータの改竄を隠蔽できます、これを"ハッシュの衝突耐性への攻撃"と呼ぶ

### 衝突耐性への攻撃

種類|Desc
-|-
強衝突耐性の突破|同一のハッシュ値を持つ全く異なるデータのペアを発見すること
弱衝突耐性の突破|ある原本データのハッシュ値と同じハッシュ値を持つデータを発見すること

参照: [https://kigyou-fullsupport.com/media/column/column-667/]
