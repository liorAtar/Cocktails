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
      this.$emit("changeComponent", "ginList");
    },
    updateToV() {
      this.$emit("changeComponent", "vodkaList");
    },
    updateToR() {
      this.$emit("changeComponent", "rumList");
    },
    updateToT() {
      this.$emit("changeComponent", "tequilaList");
    },
    updateToAll() {
      this.$emit("changeComponent", "all");
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