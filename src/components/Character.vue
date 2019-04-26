<template>
  <div v-if="newGame" class="container-character">
    <div class="">
      <p class="">{{hp}}</p>
    </div>
    <img :src="imgSrc" v-bind:alt="imgAlt">
    <button @click="attack(3, 10)">Attack</button>
    <button @click="attack(10, 20)">Special</button>
    <button @click="heal()">Heal</button>
    <button @click="toggleGame()">Reset</button>
  </div>
</template>

<script>
  import _ from 'lodash'

  export default{
    name: 'Character',
    props: ['newGame', 'toggleGame'],
    data() {
      return {
        imgSrc: require("./../assets/img/monster.gif"),
        imgAlt: "monster",
        hp: 100
      };
    },
    methods: {
      attack: function(min, max) {
        if(this.hp <= 100) {
          this.hp += - _.random(min, max, false);
          this.checkHp();
        }
      },
      heal: function() {
        if(this.hp <= 100) {
          this.hp += 10;
          this.checkHp();
        }
      },
      checkHp: function() {
        this.hp > 100 ? this.hp = 100 : this.hp;
        if(this.hp < 0) {
          this.hp = '';
          this.winner()
        }
      },
      winner: function() {
          console.log("winner");
      }
    }
  }
</script>

<style scoped>

</style>

