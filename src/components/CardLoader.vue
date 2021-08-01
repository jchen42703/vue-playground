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
      setTimeout(() => {
        this.getItems();
        resolve();
      }, 3000);
    });
  },
  methods: {
    getItems() {
      this.loading = true;
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
      console.log(`getItems: ${JSON.stringify(this.itemsList)}`);
      this.loading = false;
    },
  },
};
</script>
