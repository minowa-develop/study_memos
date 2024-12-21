# TypeScript上でのmoduleについて

## 設定項目

- package.json[type]:node実行
- tsconfig.json[module]:コンパイル後のjs

## 設定コマンド

```bash
# arg1: conpiled qrg2: run
function setting {
  CONPILED_MODULE="CommonJS"
  RUN_MODULE="commonjs"
  if [ $1 == "esm" ]; then CONPILED_MODULE="ESNext"; fi
  if [ $2 == "esm" ]; then RUN_MODULE="module"; fi
  sed -Ei "s/(\"module\": ).*/\1\"${CONPILED_MODULE}\",/" tsconfig.json
  sed -Ei "s/(\"type\": ).*/\1\"${RUN_MODULE}\",/" package.json
}
function module_test {
  src=$1
  cmp=$2
  run=$3
  setting "${cmp}" "${run}" && npx tsc
  dir="${src}-${cmp}-${run}"
  mkdir -p test
  rm -rf ./test/${dir}
  cp -r ./dist/ ./test/${dir}
  node dist/main.js > "./test/${dir}/result" 2>&1
}
```

## ts=esm,transpile=esm

- "module": "esnext"

```js
import { Data } from './Data.js';
let test = new Data();
test.setRefs("1232");
test.setScope("Agent");
test.setType("feat");
test.setSubject("修正");
test.setMessage("testmsg");
console.log(test.makeCommitMessage());
```

## ts=esm,transpile=cjs

- "module": "commonjs"

```js
"use strict";
Object.defineProperty(exports, "__esModule", { value: true });
const Data_js_1 = require("./Data.js");
let test = new Data_js_1.Data();
test.setRefs("1232");
test.setScope("Agent");
test.setType("feat");
test.setSubject("修正");
test.setMessage("testmsg");
console.log(test.makeCommitMessage());
```

## まとめ

ts|tsconfig.json[module]|package.json[type]|outputed js|result
-|-|-|-|-
ESM|**ESM**|**ESM**|ESM|success
ESM|**ESM**|**CJS**|ESM|err: Cannot use import statement outside a module
ESM|**CJS**|**ESM**|CJS|err: exports is not defined in ES module scope
ESM|**CJS**|**CJS**|CJS|success
**CJS**|ESM|**ESM**|CJS|err: require is not defined in ES module scope, you can use import instead
**CJS**|ESM|**CJS**|CJS|success
**CJS**|CJS|**ESM**|CJS|err: require is not defined in ES module scope, you can use import instead
**CJS**|CJS|**CJS**|CJS|success

※ エラーは全てrun時に出力される

- TSをCJSで記載した場合: トランスパイル結果は全てCJSとなる、そのためrunはcommonjsしか成功しない
- TSをESMで記載した場合: トランスパイル結果はtsconfigに依存する
- TSをESMで記載してトランスパイルをCJSにした場合: `Object.defineProperty(exports, "__esModule", { value: true });`が付与される

## CommonJSのモジュール作成方法

export|export|使うとき
-|-|-
ファイル全体|exports.Data = Data|let data: Data = new DataModule.Data();
特定の要素|module.exports = Data|let data: Data = new DataModule();

※ importは共通: `const Datamodule = require('./Data.js');`
※ 混合した場合はrun時にエラーとなる: `Datamodule.Data is not a constructor` or `Datamodule is not a constructor`

## ESMのモジュール作成方法

desc|import|使うとき
-|-|-
ファイル全体|import * as Datamodule from './Data.js';|let data: Datamodule.Data = new Datamodule.Data();
特定の要素|import { Data } from './Data.js';|let data: Data = new Data();
デフォルト|import Data from './Data.js';|let data: Data = new Data();

※ 基本的にexportは共通: `export class Data{`
※ デフォルトを使用する場合はexport箇所にdefaultと指定する必要がある
