<template>
  <div></div>
  <start></start>
  <questions></questions>
  <end :questions="questions" :otherVariables="otherVariables"></end>
</template>

<script>
  import Start from './components/Start.vue'
  import Questions from './components/Questions.vue'
  import End from './components/End.vue'

  export default {
    name: 'App',
    components: { Start, Questions, End },
    message: 'Vítej v dnešním kvízu! Můžeme začít?',
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
    visible: false,
    display: true,
    check_button: false,
    reset_button: false,
    wrong_answers: []
  }


</script>