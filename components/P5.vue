<template>
  <iframe
    :srcdoc="scriptHtml"
    frameborder="0"
    sandbox="allow-scripts allow-pointer-lock allow-same-origin allow-popups allow-forms allow-modals allow-downloads"
  ></iframe>
</template>
<script>
/* eslint-disable no-useless-escape */
const scriptHtml = `<!DOCTYPE html>
        <html lang="en">
          <head>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.1.9/p5.js"><\/script>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.1.9/addons/p5.sound.min.js"><\/script>
            <meta charset="utf-8" />
          </head>
          <body>
            <script>
const WIDTH = 450;
const HEIGHT = 450;
const balls = 5;
const margin = 5;
const padding = 15;
const ballSize = HEIGHT/balls + margin - padding;
const radio = ballSize/2
let x = 0;

function setup() {
  createCanvas(WIDTH, HEIGHT);
  colorMode(HSB, 400);
}

function draw() {
  background(color(30,6,42));
  noStroke();

  x = (x + 1);

  fill(color(50, 200, 200));
  circle( x + 10, radio + margin, ballSize);

  fill(color(100, 200, 200));
  circle( 2*x + 10, radio*3 + margin*2, ballSize);

  fill(color(200, 200, 200));
  circle( x*x - 10, radio*5 + margin*3, ballSize);

  fill(color(300, 200, 200));
  circle( x + 10, radio*7 + margin*4, ballSize);

  fill(color(400, 200, 200));
  circle( x + 10, radio*9 + margin*5, ballSize);
}
            <\/script>
          </body>
        </html>`
/* eslint-enable no-useless-escape */

export default {
  data() {
    return {
      scriptHtml,
    }
  },
  mounted() {},
}
</script>
<style></style>
