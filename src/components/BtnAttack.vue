<template>
  <v-btn :large="true"  :disabled="disabled"  color="red" :dark="dark"  @click="$emit('attack')">Attack</v-btn>
</template>

<script>
  export default{
   name: 'BtnAttack',
   props: ['disabled', 'dark']
  }
</script>

<style scoped>

</style>

