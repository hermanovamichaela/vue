<template>
  <div></div>
  <start></start>
  <questions></questions>
  <end></end>
</template>

<script>
  import Start from './components/Start.vue'
  import Questions from './components/Questions.vue'
  import End from './components/End.vue'

  export default {
    name: 'App',
    components: { Start, Questions, End }
  }

  
</script>