<template>
  <v-container>
    <v-card :dark="dark" class="container-log" color="blue">
      <v-card-title class="text-log-title">Log</v-card-title>
      <v-card-text class="text-log" v-for="text in log">{{text}}</v-card-text>
    </v-card>
  </v-container>
</template>

<script>
  export default{
    name: 'Log',
    props: ['log', 'dark']
  }
</script>

<style scoped>

.text-log-title {
  font-size: 3rem;
}
.text-log {
  font-size: 2rem;
  padding-left: 5rem;
  max-height: 300px;
  overflow-y: visible;
  overflow-x: hidden;
}
.container-log {
  max-height: 40rem;
  overflow-y: visible;
  overflow-x: hidden;
}
</style>

