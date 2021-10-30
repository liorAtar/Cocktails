<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="section">
          <Card
            href="#modal1"
            class="col s12 m6 l4 modal-trigger"
            v-for="item in drinksList"
            :key="item.idDrink"
            :src="item.strDrinkThumb"
            :title="item.strDrink"
            v-on:sendCurrent="getCurrentCard($event)"
          >
          </Card>
          <DrinkModal
            :drink="this.currentDrink"
            :drinkIngredients="this.currentDrinkIngredients"
            :drinkMeasurements="this.currentDrinkMeasurements"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import M from "materialize-css";
import Card from "./Card.vue";
import DrinkModal from "./DrinkModal.vue";

Vue.use(VueAxios, axios);

export default {
  name: "ItemsList",
  data() {
    return {
      currentDrink: {},
      currentDrinkIngredients: [],
      currentDrinkMeasurements: [],
    };
  },
  props: ["drinksList"],
  components: {
    Card,
    DrinkModal,
  },
  mounted() {
    M.AutoInit();
  },
  methods: {
    async getCurrentCard(title) {
      try {
        let res = await axios.get(
          `https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${title}`
        );
        this.currentDrink = JSON.parse(JSON.stringify(res.data.drinks[0]));
        this.currentDrinkIngredients = [];
        this.currentDrinkMeasurements = [];

        for (const [key, value] of Object.entries(this.currentDrink)) {
          if (key.includes("strIngredient") && value !== null) {
            this.currentDrinkIngredients.push(value);
          }
        }

        for (const [key, value] of Object.entries(this.currentDrink)) {
          if (key.includes("strMeasure") && value !== null) {
            this.currentDrinkMeasurements.push(value);
          }
        }
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>