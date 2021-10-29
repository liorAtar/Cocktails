<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="section">
          <Card
            class="col s12 m6 l4"
            v-for="item in drinksList"
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
import Card from "./Card.vue";

Vue.use(VueAxios, axios);
export default {
  name: "ItemsList",
  props: ["drinksList"],
  components: {
    Card,
  },
  mounted() {
    M.AutoInit();
  },
};
</script>