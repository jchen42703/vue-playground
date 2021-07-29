<template>
  <div>{{ name }} : {{ retailPrice }}</div>
</template>

<script>
export default {
  props: {
    name: String,
    retailPrice: String,
  },
};
</script>
