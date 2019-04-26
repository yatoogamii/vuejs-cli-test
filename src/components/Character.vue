<template>
  <div v-if="newGame" class="container-character">
  </div>
</template>

<script>
  import _ from 'lodash'

  export default{
    name: 'Character',
    props: ['newGame', 'toggleGame', 'imgSrc', 'imgAlt'],
    data() {
      return {
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
          this.hp = 0;
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

.container-character {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>

