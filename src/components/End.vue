<template>
  <button
    v-if="questions && current_question < questions.length - 1"
    @click="next"
    :disabled="!questions[current_question].user_answer"
  >
    Next
  </button>
  <button
    v-if="questions && current_question === questions.length - 1"
    @click="checkAnswers"
  >
    Vyhodnotit
  </button>
  <button @click="reset">Reset</button>
  <div v-if="results">
    <span>Špatné odpovědi: {{ wrong_answers.length }}</span>
    <span>Správné odpovědi: {{ questions.length - wrong_answers.length }}</span>
    <span>Tvá úspěšnost: {{ percentil }}%</span>
  </div>
</template>

<script>
export default {
  name: 'End',
  props: ['questions','wrong_answers','visible','message'],
  result: false
};

function checkAnswers() {
  this.visible = false;
  this.results = true;
  this.message = '';

  const wrongAnswers = [];
  const count = this.questions.length;

  for (let i = 0; i < count; i++) {
    if (this.questions[i].user_answer !== this.questions[i].correct_answer) {
      wrongAnswers.push(this.questions[i]);
    }
  }

  this.wrong_answers = wrongAnswers;
  this.percentil =
    ((this.questions.length - this.wrong_answers.length) /
      this.questions.length) *
    100;
  if (wrongAnswers.length === 0) {
    console.log('Vše správně');
  } else if (wrongAnswers.length !== count) {
    console.log('Něco je špatne');
  } else {
    console.log('Jsi looser!');
  }
}
</script>
