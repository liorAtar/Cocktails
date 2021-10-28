<template>
  <div class="card">
    <div
      class="card-image waves-effect waves-block waves-light tb-body-wrapper"
    >
      <img class="responsive-img wp-post-img" :src="src" />
      <h6 class="card-text home">{{ title }}</h6>
    </div>
  </div>
</template>

<script>
import M from "materialize-css";

export default {
  name: "Card",
  mounted() {
    M.AutoInit();
  },
  props: {
    src: String,
    title: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>