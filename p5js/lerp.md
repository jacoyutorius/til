# 線形補間

https://codepen.io/jacoyutorius/pen/oNowqpo

2つの座標を用意し、２点間の線形補間をとることでその間を移動する座標を算出することができる。

移動する点tは0〜1の間で移動する。
1に達した際に条件分岐でtの初期化を行わないと点が停止しない。


```js
let t;
let isGoForward;

function setup() {
  createCanvas(windowWidth, windowHeight);

  t = 0;
  isGoForward = true;
}

function draw() {
  clear();
  fill("white");

  const a = windowWidth/4;
  const b = windowWidth/2;

  circle(a, windowHeight/2, 20);
  circle(b, windowHeight/2, 20);

  t += 0.01;
  fill("red");
  
  if (isGoForward) {
    circle(lerp(a, b, t), windowHeight/2, 10);
  }
  else {
    circle(lerp(b, a, t), windowHeight/2, 10);
  }

  if (t > 1) {
    t = 0;
    isGoForward = !isGoForward;
  }
}
```

<p class="codepen" data-height="300" data-default-tab="html" data-slug-hash="oNowqpo" data-user="jacoyutorius" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jacoyutorius/pen/oNowqpo">
  p5js-lerp</a> by jacoyutorius (<a href="https://codepen.io/jacoyutorius">@jacoyutorius</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>