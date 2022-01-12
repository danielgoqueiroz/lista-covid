<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" href="/img/icons/favicon.ico" />
    <h1>Seus dados vazaram no Covidômetro de Floripa?</h1>
    <Busca
      msg="Descubra se você possui dados vazados no covidometrofloripa (covidometrofloripa.com.br)"
    />
  </div>
</template>

<script>
import Busca from "./components/Busca.vue";

export default {
  name: "App",
  components: {
    Busca,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
