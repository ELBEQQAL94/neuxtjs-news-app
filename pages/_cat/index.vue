<template>
  <div class="container">
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
import Post from "../../components/Post.vue";
import axios from "axios";

export default {
  components: {
    Post
  },
  data() {
    return {
      posts: []
    };
  },
  created() {
    axios
      .get(
        `http://femme.nextmedia.ma/api/get_category_posts/?slug=${this.$route.params.cat}`
      )
      .then(res => (this.posts = res.data.posts))
      .catch(err => console.log(err));
  }
};
</script>


<style scoped>
.section {
  margin: 2rem 0;
  text-align: center;
}
.section h1 {
  padding: 7px;
}
</style>

<style scoped>
.home {
  position: relative;
  margin: 2rem 0;
}
</style>