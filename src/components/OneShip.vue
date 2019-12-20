<template>
  <div class="container-one-ship">
    <button
      type="button"
      class="btn btn-primary"
      @click="doRequest"
    >Request: "https://swapi.co/api/starships/9/"</button>
    <div class="container-coin">
      <p class="content _pink" v-html="this.info"></p>
      <p class="content _green">Название: {{ this.name }}</p>
      <p class="content _green">Цена: {{ this.cost }}</p>
      <p class="content _green">Класс двигателя: {{ this.hyperdrive }}</p>
      <p class="content _green">Класс судна: {{ this.class }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "OneShip",

  data() {
    return {
      info: null,
      name: "Не известно.",
      cost: 0,
      hyperdrive: "Не известно.",
      class: "Не известно."
    };
  },

  methods: {
    doRequest: function() {
      axios.get("https://swapi.co/api/starships/9/").then(
        response => (
          (this.info = response),
          (this.name = response.data.name),
          (this.cost = response.data.cost_in_credits),
          (this.hyperdrive = response.data.hyperdrive_rating),
          (this.class = response.data.starship_class)
        )
      );
      console.log("Button REQUEST pressed.");
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../stylesheets/resets.scss";
@import "../../node_modules/bootstrap/scss/bootstrap.scss";

.container-coin {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
}

.content {
  display: block;
}

._pink {
  color: $pink;
}

._green {
  color: $green;
}
</style>