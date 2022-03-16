# いろいろなモード切替え

## angleMode

`DIGREES` を指定以降、rotateは360°で回転される。

```js
angleMode(DIGREES);
rotate(30); // 30°回転する
```

引数は `RADIANS(ラジアン)` か `DEGREES(度)`。デフォルトは `RADIANS`。
ラジアンは弧の長さ（以下の図でオレンジ色の線）。

![https://raw.githubusercontent.com/BaroqueEngine/cc/main/16/1.png](https://raw.githubusercontent.com/BaroqueEngine/cc/main/16/1.png)

refs https://zenn.dev/baroqueengine/books/a19140f2d9fc1a/viewer/35ea25#%E5%BC%A7%E5%BA%A6%E6%B3%95-%2F-%E3%83%A9%E3%82%B8%E3%82%A2%E3%83%B3


## colorMode

colorMode() には RGB や HSB のような色の体系を指定することができるが、その後に数値を指定することで色の最大値の変更をすることができる。

```js
colorMode(HSB);
```

## rectMode

rectの(x, y) が中央位置に変わる。

```js
rectMode(CENTER);
```

