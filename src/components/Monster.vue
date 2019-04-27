<template>
  <div class="monster-container">
    <h2>{{hpMonster}}</h2>
    <img src="./../assets/img/monster.gif" alt="monster character"/>
  </div>
</template>

<script>
  export default{
    name: 'Monster',
    props: ['hpMonster']
  }
</script>

<style lang="scss" scoped>
.monster-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

</style>

