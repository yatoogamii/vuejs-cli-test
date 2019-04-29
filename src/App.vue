<template>
  <main id="app" :style="darkStyle">
    <v-btn :dark="!dark" v-if="newGame" class="app__btn-dark" @click="darkmode()">{{nextMode}}</v-btn>
    <Character :death="death" :style="colorTextdarkMode" :winner="winner.name" v-if="newGame" :hpMonster="hp.monster" :hpPlayer="hp.player" >
    </Character>
    <Skills :dark="dark" :disabled="disabled" v-if="newGame" v-on:heal="heal()" v-on:attack="attack(3, 10)" v-on:spe-attack="attack(10, 20)" v-on:reset="toggleGame()"></Skills>
    <v-btn :dark="dark" :large="true" color="blue" v-if="!newGame" @click="toggleGame()" class="app__btn-new-game">New game</v-btn>
    <v-dialog :dark="dark"  v-model="dialog" width="300">
      <v-card :dark="dark"  hover>
        <v-card-title primary-title>
          <p class="headline font-weight-bold">{{ winner.name + " win" }}</p>
        </v-card-title>
        <v-card-text >Play again ?</v-card-text>
        <v-card-actions>
          <v-btn color="green" @click="reset()">Yes</v-btn>
          <v-btn color="red" @click="dialog=false">No</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <Log :dark="dark" :log="log" v-if="newGame"></Log>
  </main>
</template>

<script>
import _ from 'lodash';
import Character from './components/Character.vue';
import Skills from './components/Skills.vue';
import Log from './components/Log.vue';

export default {
  name: 'app',
  components: {
    Character,
    Skills,
    Log
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
      },
      disabled: false,
      dialog: false,
      dark: false, 
      darkStyle: '',
      colorTextdarkMode: '',
      nextMode: 'Dark',
      death: false,
      log: []
    };
  },
  methods: {
    toggleGame() {
      this.newGame ? this.newGame = false : this.newGame = true;
      this.reset();
    },
    attack(min, max) {
      let dmgPlayer = _.random(min, max);
      let dmgMonster = _.random(5, 12);
      this.addLog('attack', dmgPlayer, dmgMonster);
      this.hp.monster -= dmgPlayer; 
      this.hp.player -= dmgMonster;
      this.checkHp();
    },
    heal() {
      if ((this.hp.player + 10) > 100) {
        this.hp.player = 100;
      } else {
        this.hp.player += 10;
      }
      let dmgMonster = _.random(5, 12);
      this.addLog('heal', 10, dmgMonster);
      this.hp.player -= dmgMonster;
    },
    checkHp() {
      if (this.hp.player <= 0) {
        this.hp.player = 0;
        this.death = true;
        this.death = false;
        this.checkWinner("monster");
      }
      if (this.hp.monster <= 0) {
        this.hp.monster = 0;
        this.death = true;
        this.death = false;
        this.checkWinner("player");
      }
    },
    checkWinner(character) {
      this.winner.name = _.capitalize(character);
      this.winner.state = true;
      this.dialog = true;
      this.disabled = true;
    },
    reset() {
      for (let value in this.hp) {
        this.hp[value] = 100;
        this.winner.name = '';
        this.winner.state = false;
        this.disabled = false;
        this.dialog = false;
        this.death = false;
        this.log = [];
      }
    },
    closeDiag() {
      this.disabled = true;
    },
    darkmode() {
      this.dark = !this.dark;
      (this.darkStyle == 'background-color: #1d1d1d') ? this.darkStyle = '' : this.darkStyle = 'background-color: #1d1d1d' ;
      (this.colorTextdarkMode == 'color: white') ? this.colorTextdarkMode = '' : this.colorTextdarkMode = 'color: white';
      (this.nextMode == 'Dark' )? this.nextMode = 'Light' : this.nextMode = "Dark";
    },
    addLog(state, dmgPlayer, dmgMonster) {
      if (state == 'heal') {
        this.log.push(`Player take ${dmgPlayer} heal, Monster do ${dmgMonster} damage`);
      } else {
        this.log.push(`Player do ${dmgPlayer} damage, Monster do ${dmgMonster} damage`);
      }
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
  background-color: #cfe8ef;
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
  .app__btn-dark {
    position: absolute;
    top: 0;
  }
}
</style>
