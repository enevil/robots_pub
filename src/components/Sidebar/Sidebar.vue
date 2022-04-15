<template>
  <div class="sidebar">
    <div class="wrapper" :class="{ active: isVisible }">
      <button class="btn btn-inner" @click="toogle">≡</button>
      <p class="title">PASS DATA</p>
      <p>first_name: {{ userData?.first_name }}</p>
      <p>last_name: {{ userData?.last_name }}</p>
      <p>username: {{ userData?.username }}</p>
      <p>email: {{ userData?.email }}</p>
      <p>gender: {{ userData?.gender }}</p>
      <p>phone_number: {{ userData?.phone_number }}</p>
      <p>social_insurance_number: {{ userData?.social_insurance_number }}</p>
      <p>date_of_birt: {{ userData?.date_of_birt }}</p>
      <p>title: {{ userData?.employment?.title }}</p>
      <p>key_skill: {{ userData?.employment?.key_skill }}</p>
    </div>
    <button
      class="btn btn-outer"
      @click="toogle"
      :class="{ activeBtn: isVisible }"
    >
      ≡
    </button>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  data() {
    return {
      isVisible: false,
    };
  },

  methods: {
    toogle() {
      this.isVisible = !this.isVisible;
    },
  },
  props: {
    userData: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.wrapper {
  height: 100%;
  border: 2px solid blueviolet;
  background-color: rgba(0, 0, 0, 0.8);
  padding: 0 1rem;
}

.wrapper > p:not(:first-child) {
  margin-top: 1rem;
}

.btn {
  border: 2px solid #812020;
  padding: 0.5rem 1.5rem;
}

.btn:hover {
  background-color: #812020;
}

.btn-outer {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 100;
  transform: translateX(-100%);
  transition: 0.5s ease-in-out transform;
}

.btn-inner {
  display: none;
}

.title {
  font-size: 3rem;
}

.active {
  transform: translateX(0) !important;
}

.activeBtn {
  transform: translateX(-100%) !important;
}

@media screen and (max-width: 860px) {
  .wrapper {
    width: min-content;
  }
  .wrapper {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 100;
    transform: translateX(-100%);
    transition: 0.5s ease-in-out;
  }
  .btn-inner {
    display: block;
    position: absolute;
    top: 0;
    right: 0;
  }
  .btn-outer {
    transform: translateX(0);
  }
}
</style>
