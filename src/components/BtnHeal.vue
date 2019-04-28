<template>
  <v-btn :large="true"  :disabled="disabled"  color="green" v-on:click="$emit('heal')">Heal</v-btn>
</template>

<script>
  export default{
   name: 'Btnheal',
   props: ['disabled']
  }
</script>

<style scoped>

</style>

