<template>
  <main id="app">
    <Character :winner="winner.name" v-if="newGame" :hpMonster="hp.monster" :hpPlayer="hp.player" >
    </Character>
    <Skills v-if="newGame"v-on:heal="heal()" v-on:attack="attack(3, 10)" v-on:spe-attack="attack(10, 20)" v-on:reset="toggleGame()"></Skills>
    <button v-if="!newGame" @click="toggleGame()" class="app__btn-new-game">New game</button>
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
      },
      winner: {
        name: '',
        state: false
      }
    };
  },
  methods: {
    toggleGame() {
      this.newGame ? this.newGame = false : this.newGame = true;
      for (let value in this.hp) {
        this.hp[value] = 100;
        this.winner.name = '';
        this.winner.state = false;
      }
    },
    attack(min, max) {
      this.hp.monster -= _.random(min, max);
      this.hp.player -= _.random(6, 12);
      this.checkHp();
    },
    heal() {
      if ((this.hp.player + 10) > 100) {
        this.hp.player = 100;
      } else {
        this.hp.player += 10;
      }
    },
    checkHp() {
      if (this.hp.player <= 0) {
        this.hp.player = 0;
        this.checkWinner("monster");
      }
      if (this.hp.monster <= 0) {
        this.hp.monster = 0;
        this.checkWinner("player");
      }
    },
    checkWinner(character) {
      this.winner.name = character;
      this.winner.state = true;
    }
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

body {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

@font-face {
  font-family: 'Retro-gaming';
  src: url('./assets/font/Retro Gaming.ttf') format('truetype');
}
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Retro-gaming';

  .app__btn-new-game {
    width: 10rem;
  }
}
</style>
