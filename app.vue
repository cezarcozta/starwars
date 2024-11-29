<template>
  <div>
    <NuxtRouteAnnouncer />
    <div>
      <h1>HELLO WORLD</h1>
      <button @click="showAlert">TESTE</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    showAlert() {
      alert("Botão clicado!"); // Mensagem do alerta
    },
  },
};
</script>