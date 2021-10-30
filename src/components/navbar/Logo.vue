<template>
  <div class="cocktail-logo-container">
    <span class="cocktail-title">Cocktail</span>
    <i class="fas fa-cocktail cocktail-icon" title="Cocktail"></i>
  </div>
  <!-- <a href="#" class="logo brand-logo logo-pos"> </a> -->
</template>

<script>
import M from "materialize-css";

export default {
  name: "Logo",
  mounted() {
    M.AutoInit();
  },
};
</script>

<style scoped>
.cocktail-logo-container {
  display: flex;
  align-items: center;
  font-size: 2rem;
}
.cocktail-title {
  margin-right: 0.5rem;
}
.cocktail-icon {
  height: auto;
}
</style>