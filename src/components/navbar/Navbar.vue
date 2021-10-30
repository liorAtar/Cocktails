<template>
  <nav class="nav-extended purple">
    <div class="nav-wrapper search">
      <a href="#" class="logo brand-logo">
        Cocktails
        <i class="fas fa-cocktail" title="Cocktail"></i>
      </a>
    </div>
    <div class="nav-content navbar-flex">
      <div class="tabs-holder">
        <ul class="tabs tabs-transparent">
          <li class="tab">
            <a v-on:click="updateToAll" class="active" href="#tab">All</a>
          </li>
          <li class="tab">
            <a v-on:click="updateToG" href="#tab">Gin</a>
          </li>
          <li class="tab"><a v-on:click="updateToR" href="#tab">Rum</a></li>
          <li class="tab"><a v-on:click="updateToT" href="#tab">Tequila</a></li>
          <li class="tab"><a v-on:click="updateToV" href="#tab">Vodka</a></li>
        </ul>
      </div>
      <Search
        :currentListForSearch="this.currentListForSearch"
        v-on:serachClicked="updateSearchClicked($event)"
      />
    </div>
  </nav>
</template>

<script>
import Search from "../Search.vue";
import M from "materialize-css";

export default {
  name: "Navbar",
  mounted() {
    M.AutoInit();
  },
  props: ["currentListForSearch"],

  methods: {
    updateToG() {
      this.$emit("changeShownList", "ginList");
    },
    updateToV() {
      this.$emit("changeShownList", "vodkaList");
    },
    updateToR() {
      this.$emit("changeShownList", "rumList");
    },
    updateToT() {
      this.$emit("changeShownList", "tequilaList");
    },
    updateToAll() {
      this.$emit("changeShownList", "all");
    },
    updateSearchClicked(list) {
      this.$emit("searchedClicked", list);
    },
  },
  components: {
    Search,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.logo {
  margin-left: 10px;
}
.navbar-flex {
  display: flex;
}
.tabs-holder {
  width: 50%;
}
</style>