<template>
  <div class="home">
    <movies></movies>
  </div>
</template>

<script>
import movies from "../components/MovieList.vue";

export default {
  name: "Home",
  components: {
    movies,
  },
};
</script>
