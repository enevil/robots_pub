<template>
  <div class="bg-main">
    <div class="bg-pub container">
      <Sidebar :userData="userData" />
      <div class="content">
        <BaseHeader />
        <BaseBody
          :fetchBeer="fetchBeer"
          :beerData="beerData"
          :avatar="userData.avatar"
          :isLoading="isLoading"
        />
        <DialogFooter />
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "./components/Sidebar/Sidebar.vue";
import BaseHeader from "./components/Header/Header.vue";
import BaseBody from "./components/Body/Body.vue";
import DialogFooter from "./components/Footer/DialogFooter.vue";
import axios from "axios";

export default {
  components: {
    Sidebar,
    BaseHeader,
    BaseBody,
    DialogFooter,
  },
  data() {
    return {
      userData: {},
      beerData: {},
      isLoading: false,
    };
  },
  mounted() {
    this.fetchBeer();
    this.fetchUser();
  },
  methods: {
    timeout(ms) {
      return new Promise((resolve) => setTimeout(resolve, ms));
    },
    async fetchBeer() {
      try {
        this.isLoading = true;

        await this.timeout(2000);
        const res = await axios.get(
          "https://random-data-api.com/api/beer/random_beer"
        );
        this.beerData = res.data;
      } catch (error) {
        console.log("fetch beer error", error);
      } finally {
        this.isLoading = false;
      }
    },
    async fetchUser() {
      try {
        const res = await axios.get(
          "https://random-data-api.com/api/users/random_user"
        );
        console.log(res);
        this.userData = res.data;
      } catch (error) {
        console.log("fetch user error", error);
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html,
body,
#app {
  height: 100%;
}
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Orbitron", sans-serif;
  color: #4949d1;
}
h1 {
  font-size: clamp(3rem, 10vw, 5rem);
  letter-spacing: 0.5rem;
}
h3 {
  font-size: clamp(0.5rem, 6vw, 2rem);
}
button {
  font: inherit;
  background-color: inherit;
  cursor: pointer;
  color: inherit;
  border: none;
}
#app {
  font-family: "VT323", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: clamp(14px, 5vw, 26px);
  color: white;
}

.bg-main {
  height: 100%;
  background-color: black;
}

.bg-pub {
  height: 100%;
  background-image: url("./assets/pub.png");
  background-repeat: no-repeat;
  background-size: cover;
}

.container {
  display: grid;
  grid-template-columns: 1fr 4fr;
}

.content {
  height: 100%;
  display: grid;
  grid-template-rows: 1fr 2fr min-content;
  gap: 2rem;
}

@media screen and (max-width: 860px) {
  .container {
    display: block;
  }
}

@media screen and (max-width: 560px) {
  .content {
    grid-template-rows: min-content 1fr;
  }
}
</style>
