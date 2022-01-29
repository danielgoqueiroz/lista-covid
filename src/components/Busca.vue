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
    </b-container>
    <b-modal id="modal-1" title="Resultado">
      <h3 :style="getStyle()" class="my-4">{{ textResult.toUpperCase() }}</h3>
      <p>
        O nome <b>{{ nameUpperCase }} </b>consta como
        <b :style="getStyle()">{{ textResult.toUpperCase() }}</b> na lista dos
        dados vazados do Covidômetro.
      </p>
      <p>
        ATENÇÂO: Esta ferramenta apenas verifica se um nome consta ou não na
        lista vazada do covidômetro. Ela não verifica, caso tenham duas pessoas
        com o mesmo nome, qual é a que tem dados vazados. No entanto, só constam
        na lista pessoas que fizeram o teste de covid na rede pública de saúde
        de Florianópolis/SC.
      </p>
    </b-modal>
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
    names: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    getStyle() {
      return this.isNameOnList
        ? { color: "red", textSize: 16 }
        : { color: "green", textSize: 16 };
    },
    pesquisa() {
      if (this.name.length < 3) {
        this.msg = "Nome deve ter no mínimo 3 caracteres";
        return;
      }
      this.nameUpperCase = this.name.toUpperCase().trim();
      this.hash = md5(this.nameUpperCase);
      this.isNameOnList = names.indexOf(this.hash) > 1;
      console.log(this.names.indexOf(this.hash));
      console.log(this.isNameOnList);
      console.log(this.hash);
      if (this.isNameOnList) {
        this.textResult = `encontrado`;
        this.$bvModal.show("modal-1");
      } else {
        this.$bvModal.show("modal-1");
        this.textResult = `não encontrado`;
      }
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
