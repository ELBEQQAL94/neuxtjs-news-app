<template>
  <div>
    <Slider />
    <div class="home">
      <b-container class="bv-example-row">
        <b-row>
          <b-col v-for="post in posts" :key="post.id">
            <Post :title="post.title" :id="post.id" :url="post.thumbnail_images.medium.url" />
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import Slider from "../components/Slider.vue";
import Post from "../components/Post.vue";
import axios from "axios";

export default {
  components: {
    Slider,
    Post
  },
  head() {
    return {
      title: "news-challenge app"
    };
  },
  data() {
    return {
      posts: []
    };
  },
  created() {
    axios
      .get("http://femme.nextmedia.ma/api/get_home/")
      .then(res => (this.posts = res.data.posts))
      .catch(err => console.log(err));
  }
};
</script>

<style scoped>
.home {
  position: relative;
  margin: 2rem 0;
}
</style>
