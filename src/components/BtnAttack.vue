<template>
  <v-btn :large="true"  :disabled="disabled"  color="red" @click="$emit('attack')">Attack</v-btn>
</template>

<script>
  export default{
   name: 'BtnAttack',
   props: ['disabled']
  }
</script>

<style scoped>

</style>

