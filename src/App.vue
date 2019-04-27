<template>
  <div id="app">
    <Character :newGame="newGame" :toggleGame="toggleGame">
    <Monster></Monster>
    <User></User>
    </Character>
    <button v-if="!newGame" @click="toggleGame()">New game</button>
  </div>
</template>

<script>

import Character from './components/Character.vue';
import Monster from './components/Monster.vue';
import User from './components/User.vue';



export default {
  name: 'app',
  components: {
    Character,
    Monster,
    User
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
