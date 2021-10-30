<template>
  <div id="modal1" class="modal">
    <div class="modal-content">
      <div class="col s12">
        <h4 class="header drink-title">{{ drink.strDrink }}</h4>
        <div class="drink-img-container">
          <img class="drink-img" :src="drink.strDrinkThumb" />
        </div>
        <div class="card">
          <div class="card-content">
            <DrinkInfo
              :ingredients="drinkIngredients"
              :measurements="drinkMeasurements"
            />
          </div>
        </div>
        <p><b>Glass Type: </b>{{ drink.strGlass }}</p>
        <Instructions :instructions="drink.strInstructions" />
      </div>
    </div>
  </div>
</template>

<script>
import DrinkInfo from "../drinks/DrinkIngredients.vue";
import Instructions from "../drinks/Instructions.vue";
import M from "materialize-css";

export default {
  name: "DrinkModal",
  data() {
    return {
      ingredients: {},
    };
  },
  mounted() {
    M.AutoInit();
  },
  props: {
    drink: Object,
    drinkIngredients: Array,
    drinkMeasurements: Array,
  },
  components: {
    Instructions,
    DrinkInfo,
  },
  methods: {},
};
</script>

<style scoped>
.drink-content {
  justify-content: center;
}
.drink-title {
  text-align: center;
}
.drink-img-container {
  justify-content: center;
  display: flex;
}
.drink-img {
  width: 150px;
  height: 150px;
}
</style>