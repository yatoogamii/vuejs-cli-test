<template>
  <v-btn :dark="dark"  :large="true"  :disabled="disabled"  color="green" v-on:click="$emit('heal')">Heal</v-btn>
</template>

<script>
  export default{
   name: 'Btnheal',
   props: ['disabled', 'dark']
  }
</script>

<style scoped>

</style>

