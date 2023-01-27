<template>
  <div v-if="visible">
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
    >
      Vyhodnotit
    </button>
    <button @click="reset">Reset</button>
  </div>
  <end :questions="questions"></end>
</template>

<script>
  import End from './End.vue';

  export default {
    name: 'Questions',
    components: { End },
    data() {
      return {
        current_question: 0,
        wrong_answers: [],
        props: ['questions'],
      }
    },
    methods: {
      next() {
        this.current_question++;
      },
      reset() {
        this.current_question = 0;
        this.wrong_answers = [];
      }
    }
  };

</script>