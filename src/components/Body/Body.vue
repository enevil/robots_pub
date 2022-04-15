<template>
  <section class="ui">
    <ImgBlock :fetchBeer="fetchBeer" :avatar="avatar" />
    <BeerBox :isLoading="isLoading" :beerData="beerData" />
  </section>
</template>

<script>
import ImgBlock from "./ImgBlock/ImgBlock.vue";
import BeerBox from "./BeerBox/BeerBox.vue";
export default {
  name: "BaseBody",
  components: { ImgBlock, BeerBox },
  props: {
    fetchBeer: {
      type: Function,
      required: true,
    },
    beerData: {
      type: Object,
      required: true,
    },
    avatar: {
      type: String,
      required: true,
    },
    isLoading: {
      type: Boolean,
    },
  },
};
</script>

<style>
.ui {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

@media screen and (max-width: 580px) {
  .ui {
    grid-template-columns: 1fr;
  }
}
</style>
