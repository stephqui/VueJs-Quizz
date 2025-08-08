<template>
  <div class="container">
    <div v-if="state === 'error'">
      <p>
        Impossible de charger le quiz
      </p>
    </div>
    <div :aria-busy="state === 'loading'">
      <Quiz :quizProps="quiz" v-if="quiz" />
    </div>
  </div>

</template>

<script setup>
import { computed, onMounted, ref } from 'vue'
import Quiz from './components/Quiz.vue'
import Question from './components/Question.vue'

const quiz = ref(null)
const state = ref('loading')//Pour avoir le feedback sur l'état de chargement des données

onMounted(() => {
  fetch('../public/quiz.json')
    .then(r => {
      if (r.ok) {
        return r.json()
      }
      throw new Error('Impossible de charger le json')
    })
    .then(data => {
      quiz.value = data
      state.value = 'idle'
    })
    .catch(e => {
      state.value = 'error'
    })
})

</script>

<style>
.container{
  margin-top: 2rem;
}
</style>