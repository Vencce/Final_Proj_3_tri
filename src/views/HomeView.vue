<script>
import EmCartazComp from "../components/HomePrin/EmCartazComp.vue";
import MaisAssistidosComp from"../components/HomePrin/MaisAssistidosComp.vue";
import ProximosFilmesComp from "../components/HomePrin/ProximosFilmesComp.vue";
export default {
  components: {
    MaisAssistidosComp,
    EmCartazComp,
    ProximosFilmesComp
}
}
</script>
<template>
  <div class="carousel">
    <div
      id="carouselExampleSlidesOnly"
      class="carousel slide"
      data-ride="carousel"
    >
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img
            class="d-block w-100"
            src="@/assets/img/JokerBannerShadows.jpg"
            alt="First slide"
          />
        </div>
        <div class="carousel-item">
          <img
            class="d-block w-100"
            src="@/assets/img/DarkKnightShadows.jpg"
            alt="Second slide"
          />
        </div>
        <div class="carousel-item">
          <img
            class="d-block w-100"
            src="@/assets/img/MortalKombatShadows.jpg"
            alt="Third slide"
          />
        </div>
      </div>
    </div>
  </div>
  <MaisAssistidosComp />
  <EmCartazComp />
  <ProximosFilmesComp />
</template>

<style></style>
