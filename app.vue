<template>
  <div>
    <NuxtRouteAnnouncer />
    <div>
      <h1>HELLO WORLD</h1>
      <button @click="showAlert">TESTE</button>
      <button @click="showAlert2">Clique-me</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    showAlert() {
      alert("Botão clicado!"); // Mensagem do alerta
   
   },
   showAlert2() {
      alert("ESTOU CLICADO");
    },
  },
};
</script>




