<template>
  <div id="app">
    <headerAlborada />
    <cardPropiedades />
  </div>
</template>

<script>
import cardPropiedades from "./components/cardPropiedades.vue";
import headerAlborada from "./components/header.vue";

export default {
  name: "App",
  components: {
    cardPropiedades,
    headerAlborada,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #2a2a2a;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
