<template>
  <div>
    <div v-if="!results">Jdeme na to!</div>
    <div v-for="(question, index) in questions">
      <div v-if="index === current_question">
        {{ question.question }}
        <select v-model="question.user_answer">
          <option></option>
          <option
            v-for="answer in question.answers"
            class="question_one_option"
          >
            {{ answer }}
          </option>
        </select>
      </div>
    </div>
    <end
      v-if="results === true"
      :questions="questions"
      :wrong_answers="wrong_answers"
      :percentil="percentil"
    ></end>
    <button
      v-if="current_question < questions.length - 1"
      @click="next"
      :disabled="!questions[current_question].user_answer"
    >
      Next
    </button>
    <button
      v-if="current_question === questions.length - 1"
      @click="checkAnswers"
      :disabled="!questions[current_question].user_answer"
    >
      Vyhodnotit
    </button>
    <button @click="reset">Reset</button>
  </div>
</template>

<script>
import End from './End.vue';

export default {
  name: 'Questions',
  components: { End },
  props: ['questions'],
  data() {
    return {
      current_question: 0,
      wrong_answers: [],
      results: false,
      percentil: 0,
    };
  },
  methods: {
    next() {
      this.current_question++;
    },
    reset() {
      const count = this.questions.length;

      for (let i = 0; i < count; i++) {
        this.questions[i].user_answer = '';
      }
      this.current_question = 0;
      this.wrong_answers = [];
      this.results = false;
    },
    checkAnswers() {
      this.next();
      this.results = true;

      const wrongAnswers = [];
      const count = this.questions.length;

      for (let i = 0; i < count; i++) {
        if (
          this.questions[i].user_answer !== this.questions[i].correct_answer
        ) {
          wrongAnswers.push(this.questions[i]);
        }
      }

      this.wrong_answers = wrongAnswers;
      this.percentil =
        ((this.questions.length - this.wrong_answers.length) /
          this.questions.length) *
        100;
    },
  },
};
</script>
