<template>
  <div class="container-all-ships">
    <b-button
      @click="showAllShips"
      variant="outline-primary"
      class="button-show-all-ships"
    >Show all ships</b-button>
    <p>{{ info }}</p>

    <main>
      <div class="row">
        <div class="medium-4 columns" v-for="starship in starships" :key="starship.id">
          <div class="card">
            <div class="card-divider text-center">{{starship.name}}</div>
            <div class="card-section">
              <p>
                <em>Цена:</em>
                {{starship.cost_in_credits}}
              </p>
              <p>
                <em>Класс двигателя:</em>
                {{starship.hyperdrive_rating}}
              </p>
              <p>
                <em>Класс судна:</em>
                {{starship.starship_rank}}
              </p>

            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
const url = "https://swapi.co/api/starships/?format=json";

export default {
  name: "AllShips",

  data() {
    return {
      info: null,
      starships: []
    };
  },

  methods: {
    // loadPeople() {
    showAllShips() {
      axios.get(url).then(response => {
        this.starships = response.data.results;
        console.log("Button SHOW ALL SHIPS pressed.");
      });
    }

    // showAllShips() {
    //   axios
    //     .get("https://swapi.co/api/starships/9/")
    //     .then(response => (this.info = response));
    //   console.log("Button SHOW ALL SHIPS pressed.");
    // }
  }

  // mounted() {
  // When the Component is ready fetch the JSON from the Server Backend
  // this.loadPeople();
  // }
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