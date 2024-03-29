# base64とは

## 特徴

- 64進数を意味する言葉、画像や音声等のエンコード方式として使用される
- アルファベット(a-z, A-z)と数字(0-9)、一部の記号(+,/)の64文字(厳密には65文字※)で表す

※ データ長を揃えるためにパディングとして末尾に記号=を使用するため

## 現在の用途

- 画像データをbase64でエンコード(JSONなどで特殊文字を含まないよう)
- base64でエンコードした画像をhtmlにそのまま埋め込む(Webページの表示の際にリクエスト数を減らすため)

## 歴史

SMTPでは、ASCIIといわれる7bitで表現される英数字しか送ることができないため、メールを使って画像や音声などのデータをやりとりできない

すべてのデータを英数字で表すMIME(Multipurpose Internet Mail Extensions)という規格が登場し、その中でbase64というデータの変換方法が定められた
これによって、受信側と送信側がMIMEに則ってエンコード・デコードをすることで、メールを通して画像や音声などの送受信が可能となった

参考: [https://qiita.com/PlanetMeron/items/2905e2d0aa7fe46a36d4]
