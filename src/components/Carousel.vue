<template>
  <div class="carousel-container">
    <p>Current slide: {{currentSlide}}</p>
    <div class="carousel">
      <div class="slide" v-for="(slide, i) of slides" :style="slideStyles(i)">
        <img :src="slide.img" >
        <span>{{i + 1}}</span>
      </div>
    </div>
    <button @click="previousSlide" :disabled="currentSlide == 0">Previous</button>
    <button @click="nextSlide" :disabled="stopSlider">Next</button>
    <button @click="$emit('addSlide')">Add Slide</button>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  data () {
    return {
      currentSlide: 0,

      slides: [
        {
          img: 'http://fillmurray.com/300/200'
        },
        {
          img: 'http://via.placeholder.com/300x200'
        },
        {
          img: 'http://fillmurray.com/300/200'
        },
        {
          img: 'http://via.placeholder.com/300x200'
        },
        {
          img: 'http://fillmurray.com/300/200'
        },
        {
          img: 'http://via.placeholder.com/300x200'
        },
        {
          img: 'http://fillmurray.com/300/200'
        },
        {
          img: 'http://via.placeholder.com/300x200'
        }
      ]
    }
  },
  methods: {
    nextSlide () {
      this.currentSlide++
    },
    previousSlide () {
      this.currentSlide--
    },
    slideStyles (i) {
      let styles = {}

      styles.width = 100 / this.numOfSlides + '%'
      styles.transform = `translateX(${this.currentSlide * -100}%)`

      return styles
    }
  },
  props: {
    numOfSlides: Number
  },
  computed: {
    stopSlider: function () {
      if (this.currentSlide + this.numOfSlides >= this.slides.length) {
        return true
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .carousel {
    width: 80vw;
    margin: 0;
    white-space: nowrap;
    overflow: hidden;
  }
  .slide {
    width: 20%;
    display: inline-flex;
    flex-direction: column;
    transition: 1s all;
  }
  .slide img {
      width: 100%;
    }

</style>
