<script setup>
  import { ref, computed } from 'vue'

  const questions = ref([
    {
      quetions: 'What does PHP means?',
      answer: 0,
      answers: [
        'HyperText PreProcessor',
        'Personal HomePage',
        'Private HyperText Processor',
        'All the above are incorrect',
      ],
      selected: null
    },

    {
      quetions: 'In Object Oriented PHP, how to access attributes of a class ?',
      answer: 1,
      answers: [
        'attrub()',
        '$this->',
        'classe()',
        'return()',
      ],
      selected: null
    },

    {
      quetions: 'How to sort an array in reverse order?',
      answer: 3,
      answers: [
        'decr()',
        'desc()',
        'reverse()',
        'rsort()',
      ],
      selected: null
    },

    {
      quetions: 'What does die() do?',
      answer: 1,
      answers: [
        'Kill a process',
        'Stop the script',
        'Come out of a loop',
        'Bypass an error',
      ],
      selected: null
    },

    
    {
      quetions: 'How to get the unqiue ID of a session?',
      answer: 1,
      answers: [
        '$_SESSION["ID_PHP"]',
        'session_id()',
        'get_session()',
        '$_SESSION["ID"]',
      ],
      selected: null
    },

  ])

  const quizCompleted = ref(false);
  const currentQuestion = ref(0);
  const score = computed(() => {
    let value = 0;
    questions.value.map(q => {
      if (q.selected == q.answer) {
        value++;
      }
    })
    return value;
  })

  const getCurrentQuestion = computed(() => {
    let question = questions.value[currentQuestion.value];
    question.index = currentQuestion.value;
    return question;
  })

  const SetAnswer = e => {
    questions.value[currentQuestion.value].selected = e.target.value;
    e.target.value = null;
  }

  const NextQuestion = () => {
    if (currentQuestion.value < questions.value.length - 1) {
      currentQuestion.value++;
    } else{
      quizCompleted.value = true;
    }
  }
</script>

<template>
  <main class="app">
    <h1>PHP QUIZZ</h1>

    <section class="quiz">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
        <span class="score">Your score is {{ score }} / {{ questions.length }}</span>
      </div>
    </section>
  </main>
</template>

<style>

</style>