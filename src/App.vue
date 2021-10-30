<template>
  <div id="app">
    <HomePage />
  </div>
</template>

<script>
import HomePage from "./components/pages/HomePage.vue";

export default {
  name: "App",
  components: {
    HomePage,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
