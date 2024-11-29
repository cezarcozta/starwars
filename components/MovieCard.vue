<template>
  <div class="movie-card">
    <h3>{{ movie.title }}</h3>
    <p>{{ movie.opening_crawl }}</p>
    <nuxt-link :to="`/movie/${movie.id}`">
      <button>Ver Detalhes</button>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    movie: Object
  }
};
</script>

<style scoped>
.movie-card {
  background-color: #323232;
  color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  margin: 20px;
}

.movie-card h3 {
  color: #ffcc02;
}

button {
  background-color: #ffcc02;
  color: #000000;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
}

button:hover {
  background-color: #ffb800;
}
</style>
