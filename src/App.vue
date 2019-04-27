<template>
  <main id="app">
    <Character :newGame="newGame" :toggleGame="toggleGame" :hpMonster="hp.monster" :hpPlayer="hp.player" >
    </Character>
    <Skills v-on:heal="heal()" v-on:attack="attack(3, 10)" v-on:spe-attack="attack(10, 20)"></Skills>
    <button v-if="!newGame" @click="toggleGame()">New game</button>
  </main>
</template>

<script>

import _ from 'lodash';
import Character from './components/Character.vue';
import Skills from './components/Skills.vue';



export default {
  name: 'app',
  components: {
    Character,
    Skills,
  },
  data() {
    return {
      newGame: false,
      hp: {
        player: 100,
        monster: 100
      }
    };
  },
  methods: {
    toggleGame() {
      this.newGame ? this.newGame = false : this.newGame = true;
    },
    attack(min, max) {
      this.hp.monster -= _.random(min, max);
      this.hp.player -= _.random(6, 12);
    },
    heal() {
      if ((this.hp.player + 10) > 100) {
        this.hp.player = 100;
      } else {
        this.hp.player += 10;
      }
    },
    checkHp() {
    },
    winner() {
    }
  }
}
</script>

<style>
@font-face {
  font-family: 'Retro-gaming';
  src: url('./assets/font/Retro Gaming.ttf') format('truetype');
}
#app {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  font-family: 'Retro-gaming';
}
</style>
