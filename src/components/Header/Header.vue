<template>
  <header>
    <div>
      <h1>Kyra</h1>
      <h3>First robot pub</h3>
    </div>
    <div>
      <img src="../../assets/bottle.png" alt="bottle" />
    </div>
    <div>
      <img src="../../assets/vent.png" alt="vent" />
    </div>
    <div class="tv">
      <div class="tv-block">
        <div class="tv-screen-box">
          <div class="tv-screen"><strong>Today recomended beer</strong></div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "BaseHeader",
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  padding: 0 5%;
}

div > img {
  position: absolute;
  top: 0;
  bottom: 0;
  z-index: 0;
}

.tv {
  z-index: 10;
}

.tv-block {
  background-color: #28203d;
  border: 3px solid black;
}

.tv-screen-box {
  padding: 1rem 1rem 2rem 1rem;
}

.tv-screen {
  background-color: #210e63;
  border: 3px solid black;
  text-align: center;
  display: grid;
  place-items: center;
  padding: 10% 5%;
}

.tv-screen > strong {
  font-size: clamp(1rem, 5vw, 2rem);
  letter-spacing: 0.25rem;
}
</style>
