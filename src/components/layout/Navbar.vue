<template>
  <nav class="nav-extended purple">
    <div class="nav-wrapper">
      <a href="#" class="logo brand-logo"
        >Cocktails
        <i class="fas fa-cocktail" title="Cocktail"></i>
      </a>
    </div>
    <div class="nav-content">
      <ul class="tabs tabs-transparent">
        <li class="tab"><a class="active" href="#tab">All</a></li>
        <li class="tab">
          <a v-on:click="updateToG" href="#tab">Gin</a>
        </li>
        <li class="tab"><a href="#tab">Rum</a></li>
        <li class="tab"><a href="#tab">Tequila</a></li>
        <li v-on:click="updateToV" class="tab"><a href="#tab">Vodka</a></li>
      </ul>
    </div>
  </nav>
</template>

<script>
import M from "materialize-css";
import VodkaList from "../cocktail/VodkaList.vue";
import GinList from "../cocktail/GinList.vue";

export default {
  name: "Navbar",
  mounted() {
    M.AutoInit();
  },
  props: ["component"],
  components: {
    VodkaList,
    GinList,
  },
  methods: {
    updateToG() {
      this.$emit("changeComponent", "GinList");
    },
    updateToV() {
      this.$emit("changeComponent", "VodkaList");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.logo {
  margin-left: 10px;
}
</style>