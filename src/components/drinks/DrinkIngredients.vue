<template>
  <div>
    <h5>Ingredients</h5>
    <div class="row">
      <div class="col s12"></div>
      <div class="col s6">
        <p v-for="(ingredient, index) in ingredients" :key="index">
          {{ ingredient }}
        </p>
      </div>
      <div class="col s6">
        <p v-for="(measure, index) in measurements" :key="index">
          {{ measure }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import M from "materialize-css";

export default {
  name: "DrinkInfo",
  mounted() {
    M.AutoInit();
  },
  props: {
    ingredients: Array,
    measurements: Array,
  },
};
</script>