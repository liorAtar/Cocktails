<template>
  <form class="inline-search">
    <div class="input-field">
      <input
        class="place-text"
        id="search"
        v-on:keyup="serachClicked"
        v-model="searchtext"
        type="search"
        required
      />
      <label class="label-icon" for="search"
        ><i class="material-icons">search</i></label
      >
      <i class="material-icons">close</i>
    </div>
  </form>
</template>

<script>
import M from "materialize-css";

export default {
  name: "searchtext",
  mounted() {
    M.AutoInit();
  },
  props: ["currentListForSearch"],
  data() {
    return {
      searchtext: "",
      filteredList: [],
    };
  },
  watch: {
    // Reset the list to serach in
    searchtext: function () {
      this.filteredList = this.currentListForSearch;
    },
  },
  computed: {
    // Filter list according to serach
    filteredDrinks: function () {
      return this.filteredList.filter((drink) => {
        return drink.strDrink
          .toLowerCase()
          .match(this.searchtext.toLowerCase());
      });
    },
  },
  methods: {
    serachClicked() {
      this.$emit("serachClicked", this.filteredDrinks);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.inline-search {
  margin-left: auto;
  margin-right: 1rem;
  width: 35%;
}
.place-text {
  width: 50%;
}
</style>