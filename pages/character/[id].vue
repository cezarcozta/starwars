<template>
  <div class="character-detail">
    <h2>{{ character.name }}</h2>
    <p><strong>Cor dos olhos:</strong> {{ character.eye_color }}</p>
    <p><strong>Cor do cabelo:</strong> {{ character.hair_color }}</p>
    <p><strong>Altura:</strong> {{ character.height }} cm</p>
    <h3>Filmes</h3>
    <ul>
      <li v-for="(film, index) in character.films" :key="index">
        <a :href="film" target="_blank">Ver Filme</a>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      character: {}
    };
  },
  async mounted() {
    try {
      const response = await axios.get(`https://swapi.dev/api/films/${characterId}`);
      this.movies = response.characters.map((movie, index) => ({
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
.character-detail {
  max-width: 920px;
  margin: 20px auto;
  padding: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
}
</style>
