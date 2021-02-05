<template>
  <div class="container">
    <div class="ContainerRoot">
      <Logo />
      <h1 class="title">math_art_programming</h1>
      <P5 />
      <p class="text">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer felis
        est, rutrum at euismod sit amet, rhoncus feugiat nibh. Duis est ex,
        hendrerit id sagittis sed, varius vel lectus. Nunc condimentum euismod
        ex, ut laoreet ipsum maximus eu. Aliquam erat volutpat. Proin
        sollicitudin elit a erat pulvinar maximus. Cras in facilisis turpis.
        Mauris at nunc vitae felis rutrum blandit. Proin sed tincidunt diam, at
        semper nisl. Donec nec semper nisl. Sed fringilla tincidunt turpis quis
        pulvinar. Etiam mi sapien, tempus eu augue eu, blandit dictum ex.
        Maecenas rutrum ipsum eu odio luctus, vel commodo elit vestibulum. Donec
        consectetur libero quis sem sollicitudin, non aliquet quam eleifend. In
        luctus condimentum nunc, eget fringilla augue lacinia vitae. Nunc luctus
        facilisis est ut luctus. Proin sed commodo diam. Sed efficitur velit a
        risus auctor, ac dictum risus auctor. Nam ut eros quis lacus aliquet
        tristique ut ac purus. Ut id arcu eu leo aliquam rutrum at sit amet
        arcu. Duis cursus urna lorem, vel iaculis nisl consectetur vel. Praesent
        sed volutpat augue. Aenean tristique quis tellus eget feugiat. Fusce
        quis lectus dolor. Donec ac turpis id magna euismod euismod. Nunc lorem
        ipsum, pharetra sit amet turpis in, sagittis interdum odio. Vestibulum
        non metus ac odio blandit mattis. Curabitur nec elit sed erat blandit
        ultrices a sit amet nisl. Curabitur semper auctor sapien quis auctor.
        Praesent dapibus rutrum eros, sit amet dignissim dui rhoncus non. Donec
        fermentum, velit in mollis faucibus, ex sapien dignissim enim, vel
        iaculis quam quam quis enim. Cras sit amet nunc libero. Mauris eleifend
        aliquam nibh, in iaculis nunc pharetra in. Duis sed condimentum magna.
        Duis fringilla, enim sit amet tincidunt tincidunt, ipsum lorem luctus
        eros, dignissim consequat dolor risus vel massa. Etiam commodo leo eget
        finibus pulvinar. Aliquam in sapien aliquet, gravida sem sit amet,
        convallis urna. Mauris ut sagittis ex. Morbi nibh enim, vehicula ac
        dapibus eu, vulputate a mauris. Donec in augue eu lorem viverra iaculis.
        Vestibulum in porta lacus. Vivamus mollis, velit non tincidunt euismod,
        mi augue tempor ante, at porta justo eros placerat lacus. Sed tristique
        nisl metus, vitae pellentesque sapien mattis quis. Sed sit amet leo
        sodales, posuere quam ac, mattis nunc. Donec dapibus a odio id iaculis.
        Proin tristique ultrices scelerisque. Curabitur ante justo, posuere eget
        eros consequat, accumsan mattis nulla. Donec pharetra ligula nulla, eget
        dapibus elit aliquet et. Praesent tempus nisi id lectus facilisis
        viverra. Pellentesque sollicitudin nulla vitae libero congue, eu
        sollicitudin ipsum auctor.
      </p>
      <div class="container border">
        <div id="p5Canvas" class="p5_preview" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const script = function (p5) {
      let speed = 2
      let posX = 0

      // NOTE: Set up is here
      p5.setup = (_) => {
        p5.createCanvas(500, 500)
        const canvas = p5.createCanvas(500, 500)
        canvas.parent('p5Canvas')
        p5.ellipse(p5.width / 2, p5.height / 2, 500, 500)
      } // NOTE: Draw is here
      p5.draw = (_) => {
        p5.background(253)
        const degree = p5.frameCount * 3
        const y = p5.sin(p5.radians(degree)) * 50

        p5.push()
        p5.translate(0, p5.height / 2)
        p5.fill(5)
        p5.ellipse(posX, y, 50, 50)
        p5.pop()
        posX += speed

        if (posX > p5.width || posX < 0) {
          speed *= -1
        }
      }
    } // NOTE: Use p5 as an instance mode
    const P5 = require('p5')
    // eslint-disable-next-line
    const P5JS = new P5(script) // eslint-disable-line
  },
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: left;
  background: color(background, lighter);
}

.ContainerRoot {
  max-width: 700px;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: color(foreground, dark);
  letter-spacing: 1px;
  overflow: hidden;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.p5_preview {
  border-radius: 10px;
}

.p5Canvas {
  border-radius: 10px;
  border: 2px solid #ffb8b8;
}
</style>
