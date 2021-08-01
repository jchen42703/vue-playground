<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Loading animation + async component should display below</h3>
    <!-- async loading -->
    <AsyncCard></AsyncCard>
    <AsyncCard></AsyncCard>

    <h3>
      (Manual State Changes) Loading animation + async component should display
      below
    </h3>
    <CardLoader></CardLoader>
  </div>
</template>

<script>
import { defineAsyncComponent } from "vue";
import LoadingAnimation from "@/components/LoadingAnimation.vue";
import CardLoader from "@/components/CardLoader.vue";

const AsyncCard = defineAsyncComponent({
  loader: () => import("@/components/Card.vue"),
  loadingComponent: LoadingAnimation,
  errorComponent: LoadingAnimation,
  delay: 0,
  suspensible: false,
});

export default {
  name: "HelloWorld",
  components: {
    AsyncCard,
    CardLoader,
  },
  props: {
    msg: String,
  },
  // data() {
  //   return {
  //     itemsList: [],
  //   };
  // },
  // async mounted() {
  //   console.log("Calling mounted()....");

  //   const out = await setTimeout(() => {
  //     this.itemsList = [
  //       {
  //         name: "aijsfasjoiasjf",
  //         retailPrice: "550",
  //       },
  //       {
  //         name: "LLLLLLLL",
  //         retailPrice: "40",
  //       },
  //     ];
  //     return this.itemsList;
  //   }, 5000);
  //   console.log(`Mounted; itemsList: ${out}`);
  // },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
