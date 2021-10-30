<template>
  <div>
    <Navbar v-on:changeShownList="updateShownList($event)" />
    <Search
      :currentListForSearch="currentListForSearch"
      v-on:serachClicked="updateDrinksList($event)"
    />
    <ItemsList :drinksList="drinksList" />
  </div>
</template>

<script>
import Navbar from "../navbar/Navbar.vue";
import Search from "../Search.vue";
import ItemsList from "../ItemsList.vue";

import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import M from "materialize-css";

Vue.use(VueAxios, axios);

export default {
  name: "HomePage",
  data() {
    return {
      currentListForSearch: [],
      fetchDrinksList: [],
      drinksList: [],
      vodkaList: [],
      ginList: [],
      tequilaList: [],
      rumList: [],
      allList: [],
    };
  },
  async mounted() {
    M.AutoInit();

    // Check if the vodka list is empty
    if (this.vodkaList.length === 0) {
      await this.fetchDrinks("vodka");
      this.vodkaList = this.fetchDrinksList;
    }

    // Check if the gin list is empty
    if (this.ginList.length === 0) {
      await this.fetchDrinks("gin");
      this.ginList = this.fetchDrinksList;
    }

    // Check if the tequila list is empty
    if (this.tequilaList.length === 0) {
      await this.fetchDrinks("tequila");
      this.tequilaList = this.fetchDrinksList;
    }

    // Check if the rum list is empty
    if (this.rumList.length === 0) {
      await this.fetchDrinks("rum");
      this.rumList = this.fetchDrinksList;
    }

    // Update the first list to show to all
    this.drinksList = this.allList;

    // Update the current list to search in
    this.currentListForSearch = this.allList;
  },
  components: {
    Navbar,
    ItemsList,
    Search,
  },
  methods: {
    async fetchDrinks(drinkType) {
      this.fetchDrinksList = [];
      try {
        let res = await axios.get(
          `https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=${drinkType}`
        );
        this.fetchDrinksList = await JSON.parse(
          JSON.stringify(res.data.drinks)
        );

        // Check if drink already exist
        await this.fetchDrinksList.forEach((drink) => {
          var exists = this.allList.some((field) => {
            return field.idDrink === drink.idDrink;
          });

          if (!exists) {
            this.allList.push(drink);
          }
        });
      } catch (err) {
        console.log(err);
      }
    },
    // Update the shown list according to selected category
    updateShownList(requiredList) {
      // Check if the current tab is gin
      if (requiredList === "ginList") {
        this.drinksList = this.ginList;
      }
      // Check if the current tab is vodka
      else if (requiredList === "vodkaList") {
        this.drinksList = this.vodkaList;
      }
      // Check if the current tab is rum
      else if (requiredList === "rumList") {
        this.drinksList = this.rumList;
      }
      // Check if the current tab is tequila
      else if (requiredList === "tequilaList") {
        this.drinksList = this.tequilaList;
      }
      // Check if the current tab is all
      else if (requiredList === "all") {
        this.drinksList = this.allList;
      }

      // Update the current list to serach in it
      this.currentListForSearch = this.drinksList;
    },
    // Update the represented drinks list according to search
    updateDrinksList(list) {
      this.drinksList = list;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
