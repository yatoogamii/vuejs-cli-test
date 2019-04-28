<template>
  <div v-if="winner == 'monster' || winner == ''" class="monster-container">
    <div class="monster-container__life-bar">
      <h2>{{hpMonster}}</h2>
    </div>
    <img src="./../assets/img/monster.gif" alt="monster character"/>
  </div>
</template>

<script>
  export default{
    name: 'Monster',
    props: ['hpMonster', 'winner']
  }
</script>

<style lang="scss" scoped>
.monster-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  .monster-container__life-bar {
    background-color: green;
    text-align: center;
    width: 100%;
  }
}

</style>

