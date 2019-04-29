<template>
  <div class="user-container">
      <h2 class="user-container__name">Player</h2>
    <div class="user-container__life-bar" :style="{ width: hpPlayer + '%' }">
      <h2 class="user-container__hp">{{hpPlayer}}</h2>
    </div>
    <img v-if="winner == 'Player' || hpPlayer != 0":src="idle" alt="player character"/>
    <img v-else :src="imgDeath" alt="player character"/>
  </div>
</template>

<script>
  export default{
    name: 'User',
    props: ['hpPlayer', 'winner', 'death'],
    data() {
      return {
        idle: require('./../assets/img/player-idle.gif'),
        imgDeath: require('./../assets/img/player-death.gif')
      };
    }
    
  }
</script>

<style lang="scss" scoped>
.user-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  .user-container__life-bar {
    position: relative;
    background-color: #4caf50;
    margin-right: auto;
    height: 3rem;
    .user-container__hp {
      position: absolute;
      left: 14.4rem;
      top: 0.7rem;
    }
  }
  .user-container__name {
    margin-bottom: 1rem;
  }
}

</style>

