<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>Seus dados vazaram no Covidômetro de Floripa?</h1>
    <Busca
      msg="Descubra se você possui dados vazados no covidometrofloripa (covidometrofloripa.com.br)"
    />
    <div>
      <br /><br /><br /><br /><br /><br /><br /><br />
      <b-container>
        Esta ferramenta é gratuita e criada para que ajudar você a descobrir se
        o seu nome estava na lista vazada e
        <br />não tem ligação com o vazamento, com a Prefeitura de Florianópolis
        ou com o desenvolvimento do site do Covidômetro. <br />
        Não tem vínculo com órgãos, empresas ou entidades. <br />Também, que não
        mantém os dados armazenado, apenas a representação criptografada de
        parte da informação que possobilida fazer a busca. <br />
        A privacidade de dados pessoais é regida por Lei Federal e é um direito
        de todo cidadão.
      </b-container>
      <br />
      <p><strong> Email para contato: listacovidometro@gmail.com</strong></p>
      <b-button
        size="sm"
        to="https://github.com/danielgoqueiroz/lista-covid"
        target="_blank"
        >GitHub</b-button
      >
    </div>
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
  font-size: small;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.footer {
  position: fixed;
  bottom: 0;
  font-size: smaller;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #fcfcfc;
  font-family: sans-serif;
}
</style>
