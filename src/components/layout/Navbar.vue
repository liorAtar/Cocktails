<template>
  <nav class="nav-extended purple">
    <div class="nav-wrapper search">
      <a href="#" class="logo brand-logo">
        Cocktails
        <i class="fas fa-cocktail" title="Cocktail"></i>
      </a>
    </div>
    <div class="nav-content">
      <ul class="tabs tabs-transparent">
        <li class="tab">
          <a v-on:click="updateToAll" class="active" href="#tab">All</a>
        </li>
        <li class="tab">
          <a v-on:click="updateToG" href="#tab">Gin</a>
        </li>
        <li class="tab"><a v-on:click="updateToR" href="#tab">Rum</a></li>
        <li class="tab"><a v-on:click="updateToT" href="#tab">Tequila</a></li>
        <li class="tab"><a v-on:click="updateToV" href="#tab">Vodka</a></li>
      </ul>
    </div>
  </nav>
</template>

<script>
import M from "materialize-css";

export default {
  name: "Navbar",
  mounted() {
    M.AutoInit();
  },
  methods: {
    updateToG() {
      this.$emit("changeShownList", "ginList");
    },
    updateToV() {
      this.$emit("changeShownList", "vodkaList");
    },
    updateToR() {
      this.$emit("changeShownList", "rumList");
    },
    updateToT() {
      this.$emit("changeShownList", "tequilaList");
    },
    updateToAll() {
      this.$emit("changeShownList", "all");
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