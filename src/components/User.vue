<template>
  <div class="user-container">
    <h2>{{hp-player}}</h2>
    <img src="./../assets/img/player.gif" alt="player character"/>
  </div>
</template>

<script>
  export default{
    name: 'User',
    props: ['hp-player']
  }
</script>

<style lang="scss" scoped>
.user-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

</style>

