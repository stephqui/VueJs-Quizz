<template>
  <div class="container">
    Quiz
    <div class="margin-top:20px">
      {{ question.title }}<br />
      <br />
      {{ question.questions[0].question }}
      <br />
      <br />
      {{ question.questions[0].choices }}
      <br />
      <br />
      {{ question.questions[0].choices[1] }}
    </div>

  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue'

const question = ref([])

async function fetchQuiz() {
  await fetch('../public/quiz.json',)
    .then(r => r.json())
    .then(v => question.value = v)
}

fetchQuiz()

/* onMounted(() => {
  fetch('../public/quiz.json')
    .then(r => r.json())
    .then(v => question.value = v)
  throw new Error('pas chargé le quiz')
})*/
console.log(question)

</script>