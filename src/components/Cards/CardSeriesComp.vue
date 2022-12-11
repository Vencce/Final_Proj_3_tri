<script>
export default {
  props: {
    poster: String,
    nome_fsa: String,
    link_serie: {
      type: Object,
    },
  },
  methods: {
    UrlDoFilme(id) {
      return `/Series/${id}`;
    },
  },
};
</script>
<template>
  <div class="container">
    <img class="cardfilmes" :src="poster" />
    <div class="overlay">
      <div class="text">
        <h4 class="nome_filme">{{ nome_fsa }}</h4>
        <router-link :to="UrlDoFilme(link_serie.id)">
          <button>VER MAIS</button>
        </router-link>
      </div>
    </div>
  </div>
</template>
<style>
.filmes{
  display: flex;
  flex-direction: column;
}
.todos-filmes {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.cardfilmes {
  display: block;
  width: 100%;
}
.container {
  position: relative;
  width: 13%;
}

</style>
