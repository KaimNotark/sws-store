<template>
  <div class="container-all-ships">
    <button
      type="button"
      class="btn btn-primary"
      @click="showAllShips"
    >Show all ships</button>

    
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
    doRequest() {
      axios.get("https://swapi.co/api/starships/9/").then(
        response => (
          (this.info = response)

        )
      );
      console.log("Button SHOW ALL SHIPS pressed.");
    }
  }
};
</script>

<style lang="scss" scoped>

.container-all-ships {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
}

</style>