<template>
  <router-view />
  <AppFooter />
</template>

<script>
import AppFooter from "@/components/AppFooter.vue";
export default {
  components: {
    AppFooter,
  },
};
</script>

<style>
body {
  margin: 0;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  background-color: var(--surface-a);
  font-family: var(--font-family);
  font-weight: 400;
  color: var(--text-color);
}
</style>
