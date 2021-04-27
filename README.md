# loading secp256k1 in esbuild

This broke between `esbuild@0.11.8` and `esbuild@0.11.9`

`index.js` contains one line:

```js
const secp256k1 = require('secp256k1')
```

This throws an error with `esbuild@0.11.15` - the oldest version that does not throw an error is `esbuild@0.11.8`

## To replicate

1. Clone and build

```console
$ git clone https://github.com/achingbrain/esbuild-secp256k1.git
$ cd esbuild-secp256k1
$ npm i
$ npm run build
$ open index.html
```

2. Look in the browser console

```
index.js:1 Uncaught TypeError: Vr(...) is not a function
    at index.js:1
    at index.js:1
    at index.js:1
    at index.js:1
```

3. Build using older version

```console
$ npm install esbuild@0.11.8
$ npm run build
$ open index.html
```

No errors will be in the browser console.
