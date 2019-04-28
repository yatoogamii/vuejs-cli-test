<template>
  <div v-if="winner == 'monster' || winner == ''" class="monster-container">
    <div class="monster-container__life-bar" :style="{width: hpMonster + '%'}">
      <h2 class="monster-container__hp">{{hpMonster}}</h2>
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
    position: relative;
    background-color: #4caf50;
    margin-right: auto;
    height: 3rem;
    .monster-container__hp {
      position: absolute;
      left: 14.4rem;
      top: 0.7rem;
    }
  }
}

</style>

