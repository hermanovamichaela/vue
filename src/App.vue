<template>
  <div>
      <start :questions="questions"></start>
  </div>
</template>

<script>

  import Start from './components/Start.vue';

  export default {
    name: 'App',
    components: { Start },
    data() {
      return {
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
        ]
      }
    }
  }


</script>