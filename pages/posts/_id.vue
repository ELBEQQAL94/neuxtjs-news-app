<template>
  <div>
    <div class="single-post">
      <div class="single-post-thumbnail">
        <b-img :src="post.thumbnail_images.medium_large.url" fluid alt="Responsive image"></b-img>
      </div>
      <div class="container">
        <div class="single-post-content">
          <h1 v-html="post.title"></h1>
          <div class="text-right single-post-para" v-html="post.content"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {},
      loading: true
    };
  },
  created() {
    axios
      .get(
        `http://femme.nextmedia.ma/api/get_post/?id=${this.$route.params.id}`
      )
      .then(res => {
        this.post = res.data.post;
        this.loading = false;
        console.log(this.post);
      })
      .catch(err => console.log(err));
  }
};
</script>

<style scoped>
.single-post {
  padding: 7px;
  background: black;
  color: #ffffff
}
.single-post-thumbnail {
  width: 100%;
  text-align: center;
}
.single-post-thumbnail img {
  width: 100%;
}
.single-post-content {
  margin-top: 2rem;
}
.single-post-content h1 {
  margin: 2rem 0;
  text-align: center
}
.single-post-para {
  font-size: 1.7rem;
}

.single-post-para p {
  line-height: 0.7;
  text-align: justify;
}
</style>