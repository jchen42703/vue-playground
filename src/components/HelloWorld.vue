<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>
      (With defineAsyncComponent) Loading animation + async component should
      display below
    </h3>
    <!-- async loading -->
    <AsyncCardLoader></AsyncCardLoader>
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

const AsyncCardLoader = defineAsyncComponent({
  loader: () => import("@/components/AsyncCardLoader.vue"),
  loadingComponent: LoadingAnimation,
  delay: 0,
  suspensible: false,
});

export default {
  name: "HelloWorld",
  components: {
    AsyncCardLoader,
    CardLoader,
  },
  props: {
    msg: String,
  },
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
