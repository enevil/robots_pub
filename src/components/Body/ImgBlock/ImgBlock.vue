<template>
  <div class="img-block">
    <div class="img-container">
      <img
        :src="avatar"
        alt="robot"
        @error="imageLoadError"
        v-if="!imgIsBroken"
      />
      <p v-else>Identification error</p>
    </div>
    <button class="btn" @click="fetchBeer">Reshafl beer</button>
  </div>
</template>

<script>
export default {
  props: {
    fetchBeer: {
      type: Function,
      required: true,
    },
    avatar: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      imgIsBroken: false,
    };
  },
  methods: {
    imageLoadError() {
      this.imgIsBroken = true;
    },
  },
};
</script>

<style scoped>
.img-block {
  margin: 0 auto;
  display: grid;
  grid-template-rows: 1fr min-content;
  gap: 1rem;
}

.img-container {
  width: 50vw;
  max-width: 300px;
  max-height: 300px;
  border: 2px solid white;
  display: grid;
  place-content: center;
}

.img-container > img {
  width: 100%;
  height: 100%;
}

.btn {
  padding: 0.5rem;
  border: 2px solid #812020;
}

.btn:hover {
  background-color: #812020;
}

@media screen and (max-width: 960px) {
  .img-container {
    max-width: 250px;
    max-height: 250px;
  }
}
</style>
