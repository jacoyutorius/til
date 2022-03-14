# 等間隔に並べられた円

キャンバスを並べたい図形の数で区切ってグリッドを用意し、
その中心に図形を描画する。

https://codepen.io/jacoyutorius/pen/PoEwJBw

```js

function setup() {
  createCanvas(windowWidth, windowHeight);

  const n = 2;
  const w = width / n;
  const h = height / n;

  stroke("gray");
  strokeWeight(1);
  line(0, h, w, h);
  line(w, 0, w, h);

  let index = 0;

  for (let y = 0; y < n; y++) {
    for (let x = 0; x < n; x++) {
      const tx = w * x;
      const ty = h * y;
      index += 1;

      stroke("white");
      noFill();
      text(`(${tx}, ${ty})`, tx + 10, ty + 20);
      translate(tx, ty);
     
      fill("white");
      circle(w / 2, h / 2, 20);

      stroke("red");
      noFill();
      text(index, w / 2, h / 2);

      resetMatrix();
    }
  }
}
```