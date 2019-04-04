<template>
  <div id="app">
    <CustomInputAndResultsWithEvents />
  </div>
</template>

<script>
import CustomInputAndResultsWithEvents from './components/CustomInputAndResultsWithEvents.vue'

export default {
  name: 'app',
  components: {
    CustomInputAndResultsWithEvents
  }
}
</script>

<style>
@import 'assets/styles/tailwind.postcss';
</style>
