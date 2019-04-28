<template>
  <v-btn :large="true" :disabled="disabled" color="orange" @click="$emit('spe-attack')">Special Attack</v-btn>
</template>

<script>
  export default{
   name: 'BtnSpeAttack',
   props: ['disabled']
  }
</script>

<style scoped>

</style>

