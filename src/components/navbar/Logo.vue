<template>
  <a href="#" class="logo brand-logo">
    Cocktails
    <i class="fas fa-cocktail" title="Cocktail"></i>
  </a>
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