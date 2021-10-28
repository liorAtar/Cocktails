<template>
  <div>
    <Navbar />
    <VodkaList />
  </div>
</template>

<script>
import Navbar from "./layout/Navbar.vue";
import VodkaList from "./cocktail/VodkaList.vue";

import M from "materialize-css";

export default {
  name: "HomePage",
  mounted() {
    M.AutoInit();
  },
  components: {
    Navbar,
    VodkaList,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
