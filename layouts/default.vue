<template>
  <div>
    <NavBar />
    <Nuxt />
    <Footer />
  </div>
</template>

<style>
</style>

<script>
import NavBar from "../components/NavBar.vue";
import Footer from "../components/Footer.vue";

//get data from server APIs
export default {
  components: {
    NavBar,
    Footer
  }
};
</script>