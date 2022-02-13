<template>
  <div></div>
</template>

<script>
export default {
  props: { prediction: {} },
  computed: {
    getType() {
      return this.prediction.type;
    },
  },
};
</script>

<style scoped></style>
