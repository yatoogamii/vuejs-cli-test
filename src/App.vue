<template>
  <div id="app">
    <Character :newGame="newGame" :toggleGame="toggleGame"></Character>
    <button v-if="!newGame" @click="toggleGame()">New game</button>
  </div>
</template>

<script>
import Character from './components/Character.vue'

export default {
  name: 'app',
  components: {
    Character
  },
  data() {
    return {
      newGame: false
    };
  },
  methods: {
    toggleGame() {
      this.newGame ? this.newGame = false : this.newGame = true;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
