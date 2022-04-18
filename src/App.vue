<template>
  <h1>Problema de Mount Hall</h1>
  <div class="form">
    <div v-if="!started">
      <label for="doorsAmount">Quantas portas? </label>
      <input type="text" id="doorsAmount" size="3" v-model.number="doorsAmount">
    </div>
    <div v-if="!started">
      <label for="selectedDoor">Qual a porta premiada? </label>
      <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor">
    </div>
    <button v-if="!started" @click="started = true">Começar</button>
    <button v-if="started" @click="started = false">Reiniciar</button>
  </div>
  <div class="doors" v-if="started">
    <div v-for="i in doorsAmount" :key="i">
      <the-door :hasGift="i === selectedDoor" :number="i" />
    </div>
  </div>
</template>

<script>
import TheDoor from './components/TheDoor.vue'

export default {
  name: 'App',
  components: { TheDoor },
  data() {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: null
    }
  },
}
</script>

<style>
  * {
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
  }

  body {
    color: #fff;
    background: linear-gradient(90deg, rgba(9,131,215,1) 0%, rgba(40,245,208,1) 100%);;
  }

  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #app h1 {
    border: 1px solid #000;
    background-color: #0004;
    padding: 20px;
    margin-bottom: 60px;
  }

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form, .form input, .form button {
  margin-bottom: 10px;
  font-size: 2rem;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>