<template>
  <div class="all-ships-container">
    <b-button
      @click="showAllShips"
      variant="outline-primary"
      class="all-ships-button-show"
    >Show all ships</b-button>
    <!-- <p>{{ info }}</p> -->

    <div v-for="starship in starships" :key="starship.id">{{ starship.name }}</div>

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
// ?format=json
import axios from "axios";
const url1 = "https://swapi.co/api/starships/?page=1&format=json";
const url2 = "https://swapi.co/api/starships/?page=2&format=json";
// const url3 = "https://swapi.co/api/starships/?page=3&format=json";
// const url4 = "https://swapi.co/api/starships/?page=4&format=json";

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
      console.log("Button SHOW ALL SHIPS pressed.");

      axios
        .get(url1)
        .then(response => {
          this.starships = response.data.results;
          console.log("url1 --- " + this.starships);

          axios
            .get(url2)
            .then(response => {
              this.starships = this.starships.concat(response.data.results);
              // this.starships = this.starships +","+ response.data.results;
              console.log("url2 --- " + this.starships);
            })
            .catch(error => console.log(error));
        })
        .catch(error => console.log(error));

      // axios
      //   .get(url3)
      //   .then(response => {
      //     this.starships = this.starships + response.data.results;
      //     console.log("url3");
      //   })
      //   .catch(error => console.log(error));

      // axios
      //   .get(url4)
      //   .then(response => {
      //     this.starships = this.starships + response.data.results;
      //     console.log("url4");
      //   })
      //   .catch(error => console.log(error));
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