<template>
  <div class="monster-container">
    <h2>{{hp-monster}}</h2>
    <img src="./../assets/img/monster.gif" alt="monster character"/>
  </div>
</template>

<script>
  export default{
    name: 'monster',
    component: {

    },
    props: ['hp-monster']
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

