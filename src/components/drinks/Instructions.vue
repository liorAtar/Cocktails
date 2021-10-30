<template>
  <ul class="collapsible">
    <li>
      <div class="collapsible-header">
        <i class="fas fa-book-open"></i>Instructions
      </div>
      <div class="collapsible-body">
        <span>{{ instructions }}</span>
      </div>
    </li>
  </ul>
</template>

<script>
import M from "materialize-css";

export default {
  name: "Instructions",
  mounted() {
    M.AutoInit();
  },
  props: {
    instructions: String,
  },
};
</script>