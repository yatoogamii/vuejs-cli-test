<template>
  <div class="container-character">
    <User :winner="winner" :hp-player="hpPlayer"></User>
    <Monster :winner="winner" :hp-monster="hpMonster"></Monster>
  </div>
</template>

<script>

  import Monster from './Monster.vue';
  import User from './User.vue';


  export default {
    name: 'Character',
    components: {
      Monster,
      User
    },
    props: ['hpMonster', 'hpPlayer', 'winner'],
    methods: {
    }
  }
</script>

<style lang="scss" scoped>

.container-character {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
}
</style>

