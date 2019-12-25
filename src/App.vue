<template>
<!-- 
  как работать с запросами на API use axios
  https://ru.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html
  https://github.com/axios/axios

  вот еще такая есть штука:
  https://github.com/imcvampire/vue-axios
  но Алексей сказал, что её юзать не стоит.
 -->
  <div id="app" class="app">
    <div class="wrapper">
    
    <img alt="StarWars Ship logo" src="/images/ship-logo.png" />

    <!-- <OneShip /> -->

    <AllShips />
    </div>
  </div>
</template>

<script>
// import OneShip from "./components/OneShip.vue";
import AllShips from "./components/AllShips.vue";

export default {
  name: "app",

  components: {
    // OneShip,
    AllShips
  }
};
</script>

<style lang="scss" scoped>

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper {
  max-width: 1100px;
}
</style>
