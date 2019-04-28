<template>
  <div v-if="winner == 'player' || winner == '' " class="user-container">
    <div class="user-container__life-bar">
      <h2>{{hpPlayer}}</h2>
    </div>
    <img src="./../assets/img/player.gif" alt="player character"/>
  </div>
</template>

<script>
  export default{
    name: 'User',
    props: ['hpPlayer', 'winner']
  }
</script>

<style lang="scss" scoped>
.user-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  .user-container__life-bar {
    background-color: green;
    text-align: center;
    width: 100%;
  }
}

</style>

