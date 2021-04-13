<template>
  <loader></loader>
  <navbar></navbar>
  <router-view />
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Loader from "@/components/pageLoader.vue";

export default {
  components: {
    Navbar,
    Loader,
  },
};
</script>

<style lang="scss"></style>
