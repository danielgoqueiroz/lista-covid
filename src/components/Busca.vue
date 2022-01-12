<template>
  <div class="hello">
    <b-container>
      <p>
        O Covidômetro, ferramenta criada pela Prefeitura de Florianópolis com
        dados de pessoas infectadas por dia na cidade, disponibilizou para
        download um documento com mais de 60 dados pessoais de quem fez o teste
        para a Covid em postos de saúde e UPAs do município.<br />
      </p>
      <strong> Dados vazados:</strong><br />
      <ul>
        <li>Nome completo</li>
        <br />
        <li>Endereço</li>
        <br />
        <li>CPF</li>
        <br />
        <li>Resultado do teste de Covid</li>
        <br />
        <li>
          Nomes dos pais<br />
          Entre outros.
        </li>
        <br />
      </ul>
    </b-container>
    <b-container>
      <h4>
        Verifique se seus dados estão na lista. <br />
        Digite nome completo e sem acentuação.
      </h4>
      <b-input-group prepend="Nome" class="mt-3">
        <b-form-input v-model="name" aria-placeholder="teste"></b-form-input>
        <b-input-group-append>
          <b-button variant="success" @click="pesquisa()">Pesquisar</b-button>
        </b-input-group-append>
      </b-input-group>
      <b-jumbotron v-show="showResult" :header="titulo"> </b-jumbotron>
    </b-container>
  </div>
</template>

<script>
const md5 = require("md5");
const names = require("../assets/hash.json");
export default {
  name: "Pesquisa",
  props: {
    name: {
      type: String,
      default: "",
    },
    isNameOnList: {
      type: Boolean,
      default: false,
    },
    nameUpperCase: {
      type: String,
      default: "",
    },
    showResult: {
      type: Boolean,
      default: false,
    },
    textResult: {
      type: String,
      default: "",
    },
    hash: {
      type: String,
      default: "",
    },
    msg: String,
  },
  methods: {
    pesquisa() {
      this.showResult = false;

      if (this.name.length < 3) {
        this.msg = "Nome deve ter no mínimo 3 caracteres";
        this.showResult = false;
        return;
      }
      this.nameUpperCase = this.name.toUpperCase().trim();
      this.hash = md5(this.nameUpperCase);
      this.isNameOnList = names.indexOf(this.hash) > 1;
      if (this.response) {
        this.showResult = true;
        this.showResult = true;
        this.textResult = `Nome encontrado na lista.`;
      } else {
        this.showResult = true;
        this.showResult = true;
        this.textResult = `Nome não encontrado na lista.`;
      }
    },
  },
  computed: {
    titulo() {
      if (this.showResult) {
        if (this.name.length < 3) return "";
        return this.isNameOnList ? "Nome encontrado" : "Nome não encontrado";
      }
      return "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
