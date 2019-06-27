<template>
  <div id="example-view">
    <!-- All child <template> elements get added in here -->
    <slot></slot>
  </div>
</template>

<script>
 import * as PIXI from 'pixi.js'

 export default {
   name: 'pixi-example-page',
   data () {
     if (!window.PixiApp.example) {
       window.PixiApp.example = new PIXI.Application()
     }
     return {
       app: window.PixiApp.example,
       pixiObjects: {}
     }
   },
   mounted () {
     this.$el.appendChild(this.app.view)
     this.app.ticker.add(delta => this.$emit('tick', delta))
   }
 }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  #example-view {
    background:
      radial-gradient(
        ellipse at top left,
        rgba(255, 255, 255, 1) 40%,
        rgba(229, 229, 229, .9) 100%
      );
    height: 100vh;
    padding: 0 0;
    width: 100vw;
  }
</style>
