<template>
  <div class="post">
    <b-card :img-src="url" img-alt="Card image" img-right>
      <b-card-text>
        <nuxt-link :to="'/posts/' + id" v-html="title"></nuxt-link>
      </b-card-text>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Post",
  props: ["title", "url", "id"]
};
</script>

<style scoped>
.post {
  margin: "2rem 0";
}
</style>
