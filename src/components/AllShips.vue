<template>
  <div class="container-all-ships">
    <b-button
      @click="showAllShips"
      variant="outline-primary"
      class="button-show-all-ships"
    >Show all ships</b-button>
    <p>{{ info }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AllShips",

  data() {
    return {
      info: null
    };
  },

  methods: {
    showAllShips() {
      axios
        .get("https://swapi.co/api/starships/9/")
        .then(response => (this.info = response));
      console.log("Button SHOW ALL SHIPS pressed.");
    }
  }
};
</script>

<style lang="scss" scoped>
.container-all-ships {
  display: flex;
  justify-content: space-around;
}

.button-show-all-ships {
  width: 300px;
}
</style>