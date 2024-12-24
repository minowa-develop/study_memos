# import(esm)とrequire(cjs)両方使う方法

esmベース(package.type:moduleにする)で使用できる

```js
// use require for running environment is esm
import { createRequire } from 'module';
const require = createRequire(import.meta.url);

// import and require
import * as EData from "./Data-e.mjs";
const CData = require("./Data-c.cjs");

// instance
let edata: EData.Data = new EData.Data();
let cdata = new CData.Data();
```
