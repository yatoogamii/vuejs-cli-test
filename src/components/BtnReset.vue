<template>
  <v-btn :large="true"  color="brown" @click="$emit('reset')">Give Up</v-btn>
</template>

<script>
  export default{
   name: 'BtnReset'
  }
</script>

<style scoped>

</style>

