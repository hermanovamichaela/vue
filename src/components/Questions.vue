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
</template>

<script>
  export default {
    name: 'Questions',
    questions: [
      {
        question: 'Která herní konzole byla vytvořena dříve?',
        answers: ['PS', 'XBox'],
        correct_answer: 'PS',
        user_answer: '',
      },
      {
        question: 'Jak se jmenoval plešatý strýček z Addams Family?',
        answers: ['Tester', 'Fester'],
        correct_answer: 'Fester',
        user_answer: '',
      },
      {
        question: 'Kolik dílů mají Avengers?',
        answers: ['5', '4'],
        correct_answer: '4',
        your_answer: '',
      },
      {
        question: 'Ošemetná otázka... Marvel nebo DC?',
        answers: ['Dycky DC!', 'Dycky Marvel!'],
        correct_answer: 'Dycky Marvel!',
        your_answer: '',
      }
    ],
    current_question: 0,
    wrong_answers: []
  };
  
  function next() {
    this.current_question++;
  };

  function reset() {
    this.current_question = 0;
    this.wrong_answers = [];
  };

</script>