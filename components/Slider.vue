<template>
  <div>
    <b-carousel
      id="carousel-fade"
      style="text-shadow: 0px 0px 2px #000"
      fade
      indicators
      img-width="1024"
      img-height="480"
    >
      <b-carousel-slide
        v-for="slider in sliders"
        :key="slider.id"
        :caption="slider.title"
        :img-src="slider.thumbnail_images.medium_large.url"
      >
        <nuxt-link :to="'/posts/' + slider.id">{{slider.title}}</nuxt-link>
      </b-carousel-slide>
    </b-carousel>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      slide: 0,
      sliding: null,
      sliders: []
    };
  },
  created() {
    axios
      .get("http://femme.nextmedia.ma/api/get_home/")
      .then(res => (this.sliders = res.data.slider))
      .catch(err => console.log(err));
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    }
  }
};
</script>
