<template>
  <div class="hello">
    <label for="listaClientes">Postos Disponíveis</label>
    <select id="listaClientes" @change="onClientChange">
        <option value="" disabled selected>Selecione um posto</option>
        <option v-for="cliente in clientes" :key="cliente.id" :value="cliente.id">
            {{ cliente.nome }}
        </option>
    </select>

    <div v-if="selectedClientId">
      <label for="listaCombustiveis">Combustíveis Disponíveis</label>
      <select id="listaCombustiveis" @change="onFuelChange">
          <option value="" disabled selected>Selecione um combustível</option>
          <option v-for="combustivel in combustiveis" :key="combustivel.id" :value="combustivel.valor">
              {{ combustivel.nome }}
          </option>
      </select>
    </div>

    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="resetSelection">&times;</span>
        <p>O valor do combustível selecionado é: R$ {{ selectedFuelValue }}</p>
        <button @click="resetSelection">Retornar ao Início</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListaDeClientes',
  data() {
    return {
      clientes: [
        { id: 'Posto1', nome: 'Diamantino - CUIABA' },
        { id: 'Posto2', nome: 'Diamantino - MINAS GERAIS' },
        { id: 'Posto3', nome: 'Diamantino - RIO DE JANEIRO' },
        { id: 'Posto4', nome: 'Diamantino - PARANA' },
        { id: 'Posto5', nome: 'Diamantino - ACRE' },
        { id: 'Posto6', nome: 'Diamantino - RIO GRANDE DO SUL' },
      ],
      combustiveis: [
        { id: 'Combustivel1', nome: 'Gasolina', valor: 5.59 },
        { id: 'Combustivel2', nome: 'Etanol', valor: 3.79 },
        { id: 'Combustivel3', nome: 'Diesel', valor: 4.99 },
        { id: 'Combustivel4', nome: 'GNV', valor: 3.19 },
      ],
      selectedClientId: null,
      selectedFuelValue: null,
      showModal: false,
    };
  },
  methods: {
    onClientChange(event) {
      this.selectedClientId = event.target.value;
      this.selectedFuelValue = null;
    },
    onFuelChange(event) {
      this.selectedFuelValue = event.target.value;
      this.showModal = true;
    },
    resetSelection() {
      this.selectedClientId = null;
      this.selectedFuelValue = null;
      this.showModal = false;
    }
  }
}
</script>

<style scoped>
.hello {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  max-width: 300px;
  margin: 0 auto;
  background: linear-gradient(to right, #ff7e5f, #feb47b);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

label {
  color: #fff;
  font-size: 20px;
  margin-bottom: 10px;
}

select {
  color: #333;
  font-size: 16px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #fff;
  width: 100%;
  max-width: 280px;
  margin-bottom: 20px;
}

select:focus {
  outline: none;
  border-color: #2836fd;
  box-shadow: 0 0 7px rgb(0, 4, 255);
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: #fefefe;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  max-width: 400px;
  border-radius: 8px;
  text-align: center;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

button {
  background-color: #ff7e5f;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  margin: 10px 2px;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #feb47b;
}
</style>
