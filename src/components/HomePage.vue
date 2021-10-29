<template>
  <div>
    <Navbar v-on:changeComponent="updateComponent($event)" />
    <!-- <component v-bind:is="component"></component> -->
    <ItemsList :drinksList="drinksList" />
  </div>
</template>

<script>
import Navbar from "./layout/Navbar.vue";
import ItemsList from "./ItemsList.vue";

import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import M from "materialize-css";

Vue.use(VueAxios, axios);

export default {
  name: "HomePage",
  data() {
    return {
      drinksList: "ItemsList",
      vodkaList: [],
      ginList: [],
      tequilaList: [],
      rumList: [],
      allList: [],
    };
  },
  mounted() {
    M.AutoInit();

    if (this.vodkaList.length === 0) {
      Vue.axios
        .get("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Vodka")
        .then((res) => {
          this.vodkaList = res.data.drinks;

          this.vodkaList.forEach((element) => {
            var exists = this.allList.some((field) => {
              return field.idDrink === element.idDrink;
            });

            if (!exists) {
              this.allList.push(element);
            }
          });
        });
    }

    if (this.ginList.length === 0) {
      Vue.axios
        .get("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Gin")
        .then((res) => {
          this.ginList = res.data.drinks;

          this.ginList.forEach((element) => {
            var exists = this.allList.some((field) => {
              return field.idDrink === element.idDrink;
            });

            if (!exists) {
              this.allList.push(element);
            }
          });
        });
    }

    if (this.tequilaList.length === 0) {
      Vue.axios
        .get("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Tequila")
        .then((res) => {
          this.tequilaList = res.data.drinks;

          this.tequilaList.forEach((element) => {
            var exists = this.allList.some((field) => {
              return field.idDrink === element.idDrink;
            });

            if (!exists) {
              this.allList.push(element);
            }
          });
        });
    }

    if (this.rumList.length === 0) {
      Vue.axios
        .get("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Rum")
        .then((res) => {
          this.rumList = res.data.drinks;

          this.rumList.forEach((element) => {
            var exists = this.allList.some((field) => {
              return field.idDrink === element.idDrink;
            });

            if (!exists) {
              this.allList.push(element);
            }
          });
        });
    }

    this.drinksList = this.allList;
  },
  components: {
    Navbar,
    ItemsList,
  },
  methods: {
    updateComponent(requiredList) {
      if (requiredList === "ginList") {
        this.drinksList = this.ginList;
      } else if (requiredList === "vodkaList") {
        this.drinksList = this.vodkaList;
      } else if (requiredList === "rumList") {
        this.drinksList = this.rumList;
      } else if (requiredList === "tequilaList") {
        this.drinksList = this.tequilaList;
      } else if (requiredList === "all") {
        this.drinksList = this.allList;
        console.log(this.drinksList);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
