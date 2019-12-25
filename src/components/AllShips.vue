<template>
  <div class="all-ships-container">
    <b-button
      @click="showAllShips"
      variant="outline-primary"
      class="all-ships-button-show"
    >Show all ships</b-button>

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
            <span class="_green">{{ starship.cost_in_credits }}</span>
          </p>
          <p>
            <span class="_italic">Класс двигателя:</span>
            <span class="_green">{{ starship.hyperdrive_rating }}</span>
          </p>
          <p>
            <span class="_italic">Класс судна:</span>
            <span class="_green">{{ starship.starship_class }}</span>
          </p>
        </b-card-text>
      </b-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AllShips",

  data() {
    return {
      url: "https://swapi.co/api/starships/?page=1&format=json",

      starships: []
    };
  },

  methods: {
    async showAllShips() {
      while (this.url != null) {
        await axios
          .get(this.url)
          .then(response => {
            this.url = response.data.next;
            this.starships = this.starships.concat(response.data.results);
          })
          .catch(error => console.log(error));
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.all-ships-container {
  margin-top: 30px;
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