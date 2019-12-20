<template>
  <div id="app">
    <img alt="StarWars Ship logo" src="../public/images/ship-logo.png" />
    <button type="button" class="btn btn-primary">Request: "https://swapi.co/api/starships/9/"</button>
  </div>
</template>

<script>
export default {
  name: "app",
  components: {}
};
</script>

<style lang="scss" scoped>
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
