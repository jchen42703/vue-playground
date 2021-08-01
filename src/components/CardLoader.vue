<template>
  <div v-if="loading">
    <LoadingAnimation></LoadingAnimation>
  </div>
  <div v-else>
    <div v-for="item in itemsList" :key="item.id">
      <button>{{ item.name }} : {{ item.retailPrice }}</button>
    </div>
  </div>
</template>

<script>
import LoadingAnimation from "@/components/LoadingAnimation.vue";

export default {
  components: {
    LoadingAnimation,
  },
  data() {
    return {
      itemsList: [],
      loading: true,
    };
  },
  async mounted() {
    console.log("CardLoader mounted()");
    await new Promise((resolve) => {
      setTimeout(this.getItems, 3000);
      setTimeout(resolve, 500);
    });
  },
  methods: {
    async getItems() {
      this.loading = true;
      const out = await setTimeout(() => {
        console.log("getItems for 3 seconds");
        this.itemsList = [
          {
            name: "Joseph",
            retailPrice: "5550",
          },
          {
            name: "Joseph",
            retailPrice: "5550",
          },
        ];
      }, 3000);
      console.log(`getItems: ${out}`);
      this.loading = false;
    },
  },
};
</script>
