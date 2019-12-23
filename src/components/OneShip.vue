<template>
  <div class="container-one-ship">
    <button
      type="button"
      class="btn btn-primary"
      @click="doRequest"
    >Request: "https://swapi.co/api/starships/9/"</button>
    <div class="container-coin">
      <p class="content _pink" v-html="info"></p>
      <p class="content _green">Название: {{ name }}</p>
      <p class="content _green">Цена: {{ cost }}</p>
      <p class="content _green">Класс двигателя: {{ hyperdrive }}</p>
      <p class="content _green">Класс судна: {{ rank }}</p>
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
      rank: "Не известно."
    };
  },

  methods: {
    doRequest() {
      axios.get("https://swapi.co/api/starships/9/").then(
        response => {
          (this.info = response),
          (this.name = response.data.name),
          (this.cost = response.data.cost_in_credits),
          (this.hyperdrive = response.data.hyperdrive_rating),
          (this.rank = response.data.starship_rank)
        }
      );
      console.log("Button REQUEST pressed.");
    }
  }
};
</script>

<style lang="scss" scoped>

.container-one-ship {
  margin-top: 50px;
}

.container-coin {
  display: flex;
  flex-direction: column;
  margin-top: 30px;
}

.content {
  display: block;
}

._pink {
  color: #e83e8c;
}

._green {
  color: #28a745;
}
</style>