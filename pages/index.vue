<template>
  <div id="app">
    <v-row justify="center" align="center">
      <v-col cols="12" lg="8" md="12">
        <sheet></sheet>
        <show></show>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import sheet from '@/pages/sheet'
export default {
  components: {
    sheet,
  },
}
</script>

<style>
#app {
  font-family: 'Prompt', sans-serif;
}
</style>
