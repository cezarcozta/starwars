<template>
  <div class="movie-detail">
    <h2>{{ movie.title }}</h2>
    <p>{{ movie.opening_crawl }}</p>
    <p><strong>Diretor:</strong> {{ movie.director }}</p>
    <p><strong>Data de Lançamento:</strong> {{ movie.release_date }}</p>
    <p><strong>Produção:</strong> {{ movie.producer }}</p>

    <h3>Personagens</h3>
    <div class="character-list">
      <CharacterCard
        v-for="character in characters"
        :key="character.id"
        :character="character"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CharacterCard from '~/components/CharacterCard.vue';

export default {
  components: {
    CharacterCard
  },
  data() {
    return {
      movie: {},
      characters: []
    };
  },
  async asyncData({ params }) {
    const movieId = params.id;
    const movieResponse = await axios.get(`https://swapi.dev/api/films/${movieId}/`);
    const characterResponses = await Promise.all(
      movieResponse.data.characters.map(url => axios.get(url))
    );

    return {
      movie: movieResponse.data,
      characters: characterResponses.map(response => ({
        ...response.data,
        id: response.data.url.split('/')[5] // Adiciona ID para personagens
      }))
    };
  }
};
</script>

<style scoped>
.movie-detail {
  max-width: 920px;
  margin: 20px auto;
  padding: 20px;
}

.character-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
