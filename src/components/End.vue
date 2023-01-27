<template>
  <div>
    <p>Špatné odpovědi: {{ wrong_answers.length }}</p>
    <p>Správné odpovědi: {{ questions.length - wrong_answers.length }}</p>
    <p>Tvá úspěšnost: {{ percentil }}%</p>
  </div>
</template>

<script>
export default {
  name: 'End',
  props: ['questions','wrong_answers','percentil'],
  data() {
    return {
        result: false
    }
  },
  methods: {
  }
}
</script>
