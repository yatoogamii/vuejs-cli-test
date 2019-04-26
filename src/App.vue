<template>
  <div id="app">
    <Character :newGame="newGame" :toggleGame="toggleGame"></Character>
    <button v-if="!newGame" @click="toggleGame()">New game</button>
  </div>
</template>

<script>
import Character from './components/Character.vue';

export default {
  name: 'app',
  components: {
    Character
  },
  data() {
    return {
      newGame: false,
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
  display: flex;
  justify-content: space-evenly;
}
</style>
