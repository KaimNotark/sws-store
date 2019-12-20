<template>
  <div class="container-coin-desk">
    <p class="content _indigo" v-html="this.info"></p>
    <p class="content _orange">{{ this.value }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CoinDesk",

  data() {
    return {
      info: null,
      value: 0
    };
  },

  mounted() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then(
        response => (
          (this.info = response.data.bpi.USD.symbol),
          (this.value = response.data.bpi.USD.rate_float)
        )
      );
  }
};
</script>

<style lang="scss" scoped>
@import "../stylesheets/resets.scss";
@import "../../node_modules/bootstrap/scss/bootstrap.scss";

.container-coin-desk {
  display: flex;
  justify-content: center;
}

.content {
  display: block;
}

._indigo {
  color: $indigo;
}

._orange {
  color: $orange;
}
</style>