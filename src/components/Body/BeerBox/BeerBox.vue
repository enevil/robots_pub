<template>
  <div class="beer-box">
    <div class="main-info">
      <p class="loading" v-if="isLoading">
        Wait a minute, i'll pour you a masterpiece
      </p>
      <div class="main-props" v-else>
        <p>brand: {{ beerData.brand }}</p>
        <p>name: {{ beerData.name }}</p>
        <p>style: {{ beerData.style }}</p>
      </div>
      <div class="beer-img">
        <img
          :class="{ shake: isLoading }"
          src="../../../assets/beer.png"
          alt="beer"
        />
      </div>
    </div>
    <div class="other-props" v-if="!isLoading">
      <p>hop: {{ beerData.hop }}</p>
      <p>yeast: {{ beerData.yeast }}</p>
      <p>malts: {{ beerData.malts }}</p>
      <p>ibu: {{ beerData.ibu }}</p>
      <p>alcohol: {{ beerData.alcohol }}</p>
      <p>blg: {{ beerData.blg }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    beerData: {
      type: Object,
      required: true,
    },
    isLoading: {
      type: Boolean,
    },
  },
};
</script>

<style>
.beer-box {
  border: 2px solid blueviolet;
  background-color: rgba(0, 0, 0, 0.7);
  padding-left: 1rem;
  padding-bottom: 1rem;
  display: grid;
  align-self: start;
}

.main-info {
  display: flex;
  justify-content: space-between;
}

.main-props > p {
  margin-top: 1rem;
}

.beer-img {
  border-left: 2px solid blueviolet;
  border-bottom: 2px solid blueviolet;
  padding: 2rem;
  max-height: 150px;
}

.beer-img > img {
  height: 100%;
}

.other-props {
  margin-top: 1rem;
}

.loading {
  margin-top: 3rem;
}

.shake {
  animation-name: shake;
  animation-duration: 1s;
  animation-timing-function: ease-in-out;
  animation-iteration-count: infinite;
}

@media screen and (max-width: 580px) {
  .beer-box {
    align-self: flex-end;
  }
}

@keyframes shake {
  0% {
    transform: rotate(0);
  }
  25% {
    transform: rotate(-30deg);
  }
  50% {
    transform: rotate(0);
  }
  75% {
    transform: rotate(30deg);
  }
  100% {
    transform: rotate(0);
  }
}
</style>
