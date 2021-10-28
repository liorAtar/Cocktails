<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="section">
          <Card
            class="col s12 m6 l4"
            v-for="item in vodkaList"
            :key="item.idDrink"
            :src="item.strDrinkThumb"
            :title="item.strDrink"
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
import Card from "../layout/Card.vue";

Vue.use(VueAxios, axios);
export default {
  name: "CocktailsList",
  data() {
    return { vodkaList: undefined };
  },
  components: {
    Card,
  },
  mounted() {
    M.AutoInit();
    Vue.axios
      .get("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Vodka")
      .then((res) => {
        this.vodkaList = res.data.drinks;
        console.log(this.vodkaList);
      });
  },
};
</script>