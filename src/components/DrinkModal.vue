<template>
  <div id="modal1" class="modal">
    <div class="modal-content">
      <div class="col s12 m12">
        <h2 class="header">{{ drink.strDrink }}</h2>
        <div class="card horizontal">
          <div class="card-image">
            <img :src="drink.strDrinkThumb" />
          </div>

          <div class="card-content">
            <h5>Ingredients</h5>

            <div class="row">
              <div class="col s12"></div>
              <div class="col s6">
                <p v-for="(ingredient, index) in drinkIngredients" :key="index">
                  {{ ingredient }}
                </p>
              </div>
              <div class="col s6">
                <p v-for="(measure, index) in drinkMeasurements" :key="index">
                  {{ measure }}
                </p>
              </div>
            </div>
            <p>{{ drink.strGlass }}</p>
          </div>
        </div>
        <ul class="collapsible">
          <li>
            <div class="collapsible-header">
              <i class="material-icons">filter_drama</i>Instructions
            </div>
            <div class="collapsible-body">
              <span>{{ drink.strInstructions }}</span>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
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
  methods: {},
};
</script>