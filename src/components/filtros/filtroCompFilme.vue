<script>
import axios from "axios";
import FiltrosApi from "@/api/filtros.js";
const filtrosapi = new FiltrosApi();

export default {
  data() {
    return {
      params: {
        filme: "",
        genero: "",
      },
    };
  },
  methods: {
    buscar() {
      this.$emit("buscar", this.params);
    },
  },
  async created() {
    this.linguagens = await filtrosapi.buscarTodasAsLinguagens();
    this.classificacoes = await filtrosapi.buscarTodasAsClassificacoes();
    const { data } = await axios.get(
      "https://api.themoviedb.org/3/genre/movie/list?api_key=c4aecfa4b10ef5cc747dcad83dcdc9b2&language=pt-BR"
    );
    this.generos = data.genres;
  },
};
</script>
<template>
  <div class="todofiltro">
    <div class="filtro">
      <div class="tudo">
        <form @submit.prevent="buscar">
          <div class="sel-filtros">
            <label placeholder="Buscar por filme ou pessoa" for=""><h2>Pesquisar</h2></label>
            <input v-model="params.filme" type="text" />
          </div>
          <button class="button-fil" type="submit" @click="buscar">
            Buscar
          </button>
        </form>
      </div>
    </div>
  </div>
</template>
