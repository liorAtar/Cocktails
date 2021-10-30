<template>
  <div class="tabs-holder">
    <ul class="tabs tabs-transparent">
      <li class="tab">
        <a v-on:click="updateToAll" class="active costume-tab" href="#tab"
          >All</a
        >
      </li>
      <li class="tab">
        <a v-on:click="updateToG" href="#tab">Gin</a>
      </li>
      <li class="tab">
        <a v-on:click="updateToR" class="costume-tab" href="#tab">Rum</a>
      </li>
      <li class="tab">
        <a v-on:click="updateToT" class="costume-tab" href="#tab">Tequila</a>
      </li>
      <li class="tab">
        <a v-on:click="updateToV" class="costume-tab" href="#tab">Vodka</a>
      </li>
    </ul>
  </div>
</template>

<script>
import M from "materialize-css";

export default {
  name: "Tabs",
  mounted() {
    M.AutoInit();
  },
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
  },
};
</script>

<style scoped>
.tabs-holder {
  padding-top: 10px;
}
.costume-tab {
  padding: 0 10px !important;
}
</style>