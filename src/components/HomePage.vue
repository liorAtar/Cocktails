<template>
  <div>
    <Navbar v-on:changeComponent="updateComponent($event)" />
    <component v-bind:is="component"></component>
  </div>
</template>

<script>
import Navbar from "./layout/Navbar.vue";
import VodkaList from "./cocktail/VodkaList.vue";
import GinList from "./cocktail/GinList.vue";
import RumList from "./cocktail/RumList.vue";

import M from "materialize-css";

export default {
  name: "HomePage",
  data() {
    return {
      component: "VodkaList",
    };
  },
  mounted() {
    M.AutoInit();
  },
  components: {
    Navbar,
    VodkaList,
    GinList,
    RumList,
  },
  methods: {
    updateComponent(component) {
      this.component = component;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
