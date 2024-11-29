<template>
  <div class="home">
    <h2>Filmes da Saga Star Wars</h2>
    <div class="movie-list">
      <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import MovieCard from '~/components/MovieCard.vue';

export default {
  components: {
    MovieCard
  },
  data() {
    return {
      movies: []
    };
  },
  async mounted() {
    try {
      const response = await axios.get('https://swapi.dev/api/films/');
      this.movies = response.data.results.map((movie, index) => ({
        ...movie,
        id: index + 1 // Adiciona o ID do filme para navegação
      }));
    } catch (error) {
      console.error("Erro ao carregar filmes", error);
    }
  }
};
</script>

<style scoped>
.home {
  max-width: 920px;
  margin: 20px auto;
  padding: 20px;
}

.movie-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
