<template>
  <div>{{ message }}</div>
  <div v-if="display">
    <button @click="start">Start</button>
    <button @click="end">Konec</button>
  </div>
  <questions v-if="visible" :questions="questions"></questions>
</template>

<script>
  import Questions from './Questions.vue'

  export default {
    name: 'Start',
    components: { Questions },
    props:['questions'], 
    data() {
      return {
        message: 'Vítej v dnešním kvízu! Můžeme začít?',
        visible: false,
        display: true,
        check_button: false,
        reset_button: false,
      }
    },
    methods: {
      start() {
        this.message = '';
        this.visible = true;
        this.display = false;
        this.check_button = true;
        this.reset_button = true;
      }
    }
  };
</script>