<template>
  <button>{{ name }} : {{ retailPrice }}</button>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      retailPrice: "",
    };
  },
  async created() {
    console.log("Calling Card created()....");

    const out = await setTimeout(() => {
      console.log("Card timeout 5 seconds");
      this.name = "Joseph";
      this.retailPrice = "550";
    }, 5000);
    console.log("created", out);
  },
};
</script>
