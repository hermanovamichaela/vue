<template>
  <div>{{ message }}</div>
  <div v-if="display">
    <button @click="start">Start</button>
    <button @click="end">Konec</button>
  </div>
</template>

<script>
  export default {
    name: 'Start',
    message: 'Vítej v dnešním kvízu! Můžeme začít?',
    visible: false,
    display: true,
    check_button: false,
    reset_button: false
  };

  function start() {
      this.message = 'Jdeme na to!';
      this.visible = true;
      this.display = false;
      this.check_button = true;
      this.reset_button = true;
  };

  function end() {
    this.message = 'Měj se hezky :)';
    this.visible = false;
    this.display = false;
  };
</script>