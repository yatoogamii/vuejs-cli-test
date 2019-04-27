<template>
  <div v-if="newGame" class="container-character">
    <Monster></Monster>
    <User></User>
  </div>
</template>

<script>

  import _ from 'lodash'; 
  import Monster from './Monster.vue';
  import User from './User.vue';


  export default {
    name: 'Character',
    components: {
      Monster,
      User
    },
    props: ['newGame', 'toggleGame'],
    data() {
      return {
        hp: {
          player: 100,
          monster: 100
        }
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
          this.hp = 0;
          this.winner()
        }
      },
      winner: function() {
      }
    }
  }
</script>

<style lang="scss" scoped>

.container-character {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>

