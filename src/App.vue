<template>
<!-- 
  как работать с запросами на API use axios
  https://ru.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html
  https://github.com/axios/axios

  вот еще такая есть штука:
  https://github.com/imcvampire/vue-axios
  пока не ясно, стоит ее юзать или нет
 -->
  <div id="app">
    <img alt="StarWars Ship logo" src="../public/images/ship-logo.png" />

    <CoinDesk />

    <OneShip />
  </div>
</template>

<script>
import CoinDesk from "./components/CoinDesk.vue";
import OneShip from "./components/OneShip.vue";

export default {
  name: "app",
  components: {
    CoinDesk,
    OneShip
  }
};
</script>

<style lang="scss" scoped>
@import "./stylesheets/resets.scss";
@import "../node_modules/bootstrap/scss/bootstrap.scss";

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
