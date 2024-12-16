# JSのmoduleについて

CommonJSとかES6とかごちゃごちゃしてきたのでまとめた

## 用語整理

- ECMA Script(ES)
  Javascriptの仕様、JavaScript標準化団体のECMAによって定められている
  拡張子は`.mjs`
- ES Modules(ESM)
  ES仕様のモジュールシステムの仕様
- CommonJS(CJS)
  Javascriptの各種仕様を定めることを目標にしたプロジェクト(広義の意味)
  この中にCJS独自のモジュールシステム仕様(狭義の意味)が定められている
  拡張子は`.cjs`
  参照: <https://ja.wikipedia.org/wiki/CommonJS>

## 比較

仕様|CJS|ES
-|-|-
モジュールシステム|CJS,CJS Module|ESM
拡張子|.cjs|mjs
package.jsonのtype|commonjs|module
module読み込み方法|const 変数 = require(file)|import 変数 from file
同期|同期的|非同期
呼び出し時の拡張子|省略可能|省略不可
ブラウザ上でhtmlのscript|使用不可|type="module"
トップレベルのawait|使用不可|使用可能
実行タイミング|即時実行|はてな

参考: <https://qiita.com/kohki_takatama/items/6949980d61f8c02ffd8d>

## 互換性

呼び出す側はESで記載した方が楽

import|export|使用可能
-|-|-
CJS|ES|不可
ES|CJS|可能

## ESから呼び出す方法

desc|script
-|-
ファイル全体を呼び出す|import * as 変数名 from 'ファイル名';
関数のみを指定して呼び出す|import { func1 } from 'ファイル名';
