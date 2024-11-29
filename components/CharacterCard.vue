<template>
  <div class="character-card">
    <h4>{{ character.name }}</h4>
    <nuxt-link :to="`/character/${character.id}`">
      <button>Ver Mais</button>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    character: Object
  }
};
</script>

<style scoped>
.character-card {
  background-color: #323232;
  color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  margin: 10px;
}

.character-card h4 {
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
