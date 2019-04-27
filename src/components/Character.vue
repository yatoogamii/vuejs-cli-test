<template>
  <div v-if="newGame" class="container-character">
    <User :hp-player="hpPlayer"></User>
    <Monster :hp-monster="hpMonster"></Monster>
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
    props: ['newGame', 'toggleGame', 'hpMonster', 'hpPlayer'],
    methods: {
    }
  }
</script>

<style lang="scss" scoped>

.container-character {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
}
</style>

