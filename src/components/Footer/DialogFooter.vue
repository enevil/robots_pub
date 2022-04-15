.
<template>
  <footer>
    <div class="dialog-container">
      Bartender: good day wanderer, though there is not a single bird outside
      the window, only iron pieces of metal ... do you want something stronger?
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style scoped>
footer {
  display: grid;
  align-items: flex-end;
}
.dialog-container {
  width: 70%;

  border: 1px solid rgb(128, 30, 30);
  padding: 0.5rem 1rem;
}

@media screen and (max-width: 580px) {
  footer {
    display: none;
  }
}
</style>
