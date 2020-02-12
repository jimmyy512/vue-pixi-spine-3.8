<template>
  <div class="hello">

  </div>
</template>

<script>
import * as PIXI from 'pixi.js'
import '@/js/pixi_3.8/pixi-spine'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted () {
    var app = new PIXI.Application()

    document.body.appendChild(app.view)

    app.loader
      .add('spineCharacter', '/static/spine/girl_blue.json')
      .load(function (loader, resources) {
        // var animation = new PIXI.spine.Spine(resources.spineCharacter.spineData)

        // // add the animation to the scene and render...
        // app.stage.addChild(animation)

        // run
        console.log(resources.spineCharacter)
        var animation = new PIXI.spine.Spine(resources.spineCharacter.spineData)
        animation.x = 200
        animation.y = 300
        if (animation.state.hasAnimation('animation')) {
          // run forever, little boy!
          animation.state.setAnimation(0, 'animation', true)
          // dont run too fast
          animation.state.timeScale = 1
        }
        app.stage.addChild(animation)
        app.start()
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
