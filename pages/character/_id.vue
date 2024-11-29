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
  async asyncData({ params }) {
    const characterId = params.id;
    const response = await axios.get(`https://swapi.dev/api/people/${characterId}/`);
    return {
      character: response.data
    };
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
