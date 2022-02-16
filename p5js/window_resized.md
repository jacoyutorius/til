# 画像の表示とウィンドウサイズに合わせて画像位置の調整

**windowResizedを使ったほうが良さそう。**

```js
let img;

function preload() {
  img = loadImage("https://d3avprx962x2m0.cloudfront.net/public/871557238.jpg");
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  imageMode(CENTER);
  
  const x = windowWidth / 2;
  const y = windowHeight / 2;
  image(img, x, y);
}

function windowResized() {
  clear();
  const x = windowWidth / 2;
  const y = windowHeight / 2;
  image(img, x, y);
}
```