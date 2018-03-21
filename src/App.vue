<template>
  <div id="app">
    This has 2 slides:
    <Carousel :numOfSlides="numOfSlides" @addSlide="numOfSlides++"/>

  </div>
</template>

<script>
import Carousel from './components/Carousel'

export default {
  name: 'App',
  components: {
    Carousel
  },
  data () {
    return {
      numOfSlides: 2
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
