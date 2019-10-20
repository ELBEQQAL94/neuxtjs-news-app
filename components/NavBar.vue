<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <div class="container">
        <b-navbar-brand href="/">VUEJS CHALLENGE</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto" v-for="category in categories" :key="category.id">
            <nuxt-link
              :to="'/' + category.slug"
              class="nav-link"
            >{{category.title}}</nuxt-link>
          </b-navbar-nav>
        </b-collapse>
      </div>
    </b-navbar>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  name: "NavBar",
  data() {
    return {
      categories: []
    };
  },
  created() {
    axios
      .get("http://femme.nextmedia.ma/api/get_category_index")
      .then(res => (this.categories = res.data.categories))
      .catch(err => console.log(err));
  }
};
</script>