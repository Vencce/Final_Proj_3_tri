<script>
import axios from "axios";
import FiltrosApi from "@/api/filtros.js";
const filtrosapi = new FiltrosApi();

export default {
  data() {
    return {
      params: {
        serie: "",
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
    const { data } = await axios.get(
      "https://api.themoviedb.org/3/genre/tv/list?api_key=c4aecfa4b10ef5cc747dcad83dcdc9b2&language=pt-BR"
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
            <label placeholder="Buscar" for=""><h2>Pesquisar</h2></label>
            <input v-model="params.serie" type="text" />
          </div>
          <button class="button-fil" type="submit" @click="buscar">
            Buscar
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<style>
form{
  display: flex;
}
input, select {
  height: 25px;
  border: none;
  width: 100%;
  border-radius: 10px;
}
.tudo {
  display: flex;
  align-items: center;
}
label{
  font-size: 1.1em;
  font-weight: bold;
  margin-bottom: 5px;
  width: 220px;
}
.todofiltro{
  margin: 0px 57px 10px 57px;
}
.filtro{
  color: rgb(255, 255, 255);
  padding: 25px;
  border-radius: 15px;
  display: flex;
  background-color: rgb(82, 76, 76);
  flex-direction: column;
}
.button-fil{
  width: 60px;
  height: 30px;
  border-radius: 8px;
  border: none;
  margin-top: 48px;
  margin-left: 15px;
}
</style>
