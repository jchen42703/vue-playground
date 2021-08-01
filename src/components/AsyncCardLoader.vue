<template>
  <div v-for="item in itemsList" :key="item.id">
    <button>{{ item.name }} : {{ item.retailPrice }}</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      itemsList: [],
    };
  },
  async mounted() {
    console.log("AsyncCardLoader mounted()");
    await this.getItems();
  },
  methods: {
    async getItems() {
      this.itemsList = await new Promise((resolve) => {
        setTimeout(() => {
          const items = [
            {
              name: "Other item",
              retailPrice: "5550",
            },
            {
              name: "item1",
              retailPrice: "5550",
            },
          ];
          resolve(items);
        }, 3000);
      });
      console.log(`getItems: ${JSON.stringify(this.itemsList)}`);
    },
  },
};
</script>
