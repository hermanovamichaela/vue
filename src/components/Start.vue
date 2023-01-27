<template>
  <div>{{ message }}</div>
  <div v-if="display">
    <button @click="start">Start</button>
    <button @click="end">Konec</button>
  </div>
  <questions v-if="visible"></questions>
</template>

<script>
  import Questions from './Questions.vue'

  export default {
    name: 'Start',
    components: { Questions },
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
        this.message = 'Jdeme na to!';
        this.visible = true;
        this.display = false;
        this.check_button = true;
        this.reset_button = true;
      },
      end() {
        this.message = 'Měj se hezky :)';
        this.visible = false;
        this.display = false;
      },
    }
  };
</script>