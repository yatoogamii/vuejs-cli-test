<template>
  <v-btn :dark="dark"  :large="true"  color="brown" @click="$emit('reset')">Give Up</v-btn>
</template>

<script>
  export default{
   name: 'BtnReset',
   props: ['dark']
  }
</script>

<style scoped>

</style>

