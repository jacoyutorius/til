# いろいろなモード切替え

## angleMode

`DIGREES` を指定以降と、rotateは360°で回転される。

```js
angleMode(DIGREES);
rotate(30); // 30°回転する
```

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

