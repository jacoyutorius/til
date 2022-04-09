# require.context の使い方

指定したディレクトリ配下のモジュールをすべて読み込む。
第2引数はサブディレクトリのファイルを読み込むかどうか。

```bash
You can create your own context with the require.context function. It allows you to pass three parameters:

the directory to match within,
a boolean flag to include or exclude subdirectories,
a regular expression to match files against.
```

```js
require.context(directory, useSubdirectories = false, regExp = /^\.\//)
```

[https://github.com/webpack/docs/wiki/context#requirecontext](https://github.com/webpack/docs/wiki/context#requirecontext)