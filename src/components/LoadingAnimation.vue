<template>
  <p class="text">LOADING...</p>
</template>

<script>
export default {
  name: "LoadingAnimation",
  created() {
    console.log("LOADING ANIMATION RENDERED");
  },
  mounted() {
    console.log("LOADING ANIMATION MOUNTED");
  },
};
</script>

<style scoped>
.text {
  font-size: 30px;
  color: black;
  z-index: 40;
}
</style>
