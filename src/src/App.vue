<template>
  <div id="app">
    <header class="header">
      <img alt="Logo" src="./assets/gas.png" height="200px">
    </header>
    <ListaDeClientes />
    <footer class="footer">
      <button @click="showMessage('Endereço da Sede')">Endereço da sede</button>
      <button @click="showMessage('Contato')">Contato</button>
      <button @click="showMessage('Dúvidas')">Dúvidas</button>
      <p v-if="showContactMessage">{{ contactMessage }}</p>
    </footer>
  </div>
</template>

<script>
import ListaDeClientes from './components/ListaDeClientes.vue';

export default {
  name: 'App',
  components: {
    ListaDeClientes
  },
  data() {
    return {
      showContactMessage: false,
      contactMessage: ''
    };
  },
  methods: {
    showMessage(contact) {
      this.showContactMessage = true;
      this.contactMessage = `${contact} ainda não implementado.`;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: linear-gradient(to bottom, #ff7e5f, #feb47b); /* Fundo gradiente */
}

.header {
  background: linear-gradient(to right, #ff7e5f, #feb47b); /* Cabeçalho gradiente */
  padding: 20px;
}

.footer {
  margin-top: 20px;
  padding: 20px;
  background-color: #333;
  color: #fff;
}

.footer button {
  background-color: #ff7e5f;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  margin: 10px 2px;
  cursor: pointer;
  border-radius: 4px;
}

.footer button:hover {
  background-color: #feb47b;
}
</style>
