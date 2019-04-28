<template>
  <div v-if="winner == 'player' || winner == '' " class="user-container">
    <div class="user-container__life-bar" :style="{ width: hpPlayer + '%' }">
      <h2 class="user-container__hp">{{hpPlayer}}</h2>
    </div>
    <img src="./../assets/img/player.gif" alt="player character"/>
  </div>
</template>

<script>
  export default{
    name: 'User',
    props: ['hpPlayer', 'winner'],
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
}

</style>

