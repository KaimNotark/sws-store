<template>
  <div class="all-ships-container">
    <b-button
      @click="showAllShips"
      variant="outline-primary"
      class="all-ships-button-show"
    >Show all ships</b-button>
    <!-- <p>{{ info }}</p> -->

    <div class="cards-container">
      <b-card
        class="cards-card"
        border-variant="dark"
        :header="starship.name"
        v-for="starship in starships"
        :key="starship.id"
      >
        <b-card-text class="cards-content">
          <p>
            <span class="_italic">Цена:</span>
            <span class="_green"> {{ starship.cost_in_credits }} </span>
          </p>
          <p>
            <span class="_italic">Класс двигателя:</span>
            <span class="_green"> {{ starship.hyperdrive_rating }} </span>
          </p>
          <p>
            <span class="_italic">Класс судна:</span>
            <span class="_green"> {{ starship.starship_class }} </span>
          </p>
        </b-card-text>
      </b-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const url = "https://swapi.co/api/starships/?format=json";

export default {
  name: "AllShips",

  data() {
    return {
      // info: null,
      starships: []
    };
  },

  methods: {
    showAllShips() {
      axios.get(url).then(response => {
        this.starships = response.data.results;
        console.log("Button SHOW ALL SHIPS pressed.");
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.all-ships-container {
}

.all-ships-button-show {
  width: 300px;
}

.cards-container {
  display: flex;
  flex-direction: column;
}

.cards-card {
  margin: 10px;
  font-weight: bold;
}

.cards-content {
  font-weight: normal;
}

._italic {
  font-style: italic;
}
._green {
  color: green;
}
</style>