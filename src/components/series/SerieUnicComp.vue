<script>
import axios from "axios";
import SeriesApi from "../../api/series.js";
import FiltrosApi from "../../api/filtros.js";
const filtrosapi = new FiltrosApi();
const seriesapi = new SeriesApi();
export default {
  data() {
    return {
      name: {},
      serie: "",
    };
  },
  components: {},
  props: {
    poster: String,
    nome_serie: String,
    serie_id: Number,
    sinopse_serie: String,
    duracao: Number,
  },
  async created() {
    this.series = await seriesapi.BuscarTodasAsSeries();
    const url = `https://api.themoviedb.org/3/tv/${this.id}?api_key=df0a1976ab5aa969146a8dbff08f0123&language=pt-BR`;
    const { data } = await axios.get(url);
    this.serie = data;
  },
  methods: {
    getPosterUrl(profile_path) {
      return `https://image.tmdb.org/t/p/w500${profile_path}`;
    },
  },
};
</script>
<template>
  <main>
    <div class="lds">
      <div class="Esq">
        <div>
            <img class="Img_Filme" :src="poster" alt="">
            <h2 class="Tit_Filme">{{ nome_serie }}</h2>
            <h3>{{ duracao }} temporada(s)</h3>
            <p class="Desc_Filme">{{ sinopse_serie }}</p>
          </div>
        </div>
        <div class="r-dir">
          <div class="img-dir">
              <div class="dentro-img"></div>
              <div class="texto"></div>
          </div>
          <div class="img-dir">
              <div class="dentro-img"></div>
          </div>
          <div class="img-dir">
              <div class="dentro-img"></div>
          </div>
        </div>
        <div class="l-dir">
          <div class="img-dir">
              <div class="dentro-img"></div>
              <div class="texto"></div>
          </div>
          <div class="img-dir">
              <div class="dentro-img"></div>
          </div>
          <div class="img-dir">
              <div class="dentro-img"></div>
          </div>
        </div>
      </div>
  </main>
</template>
