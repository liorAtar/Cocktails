<template>
  <nav class="nav-extended purple">
    <div class="nav-wrapper search">
      <Logo />
    </div>
    <div class="nav-content navbar-flex">
      <Tabs v-on:changeShownList="updateListName($event)" />
      <Search
        :currentListForSearch="this.currentListForSearch"
        v-on:serachClicked="updateSearchClicked($event)"
      />
    </div>
  </nav>
</template>

<script>
import Logo from "./Logo.vue";
import Tabs from "./Tabs.vue";
import Search from "./Search.vue";
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
    updateListName(listName) {
      this.$emit("changeShownList", listName);
    },
  },
  components: {
    Search,
    Tabs,
    Logo,
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