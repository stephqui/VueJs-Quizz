<template>
  <div class="container">
    Quiz
    <br /><br />
   
    <div v-if="loadingState === 'error'">
      <p>
        Impossible de charger le quiz
      </p>
    </div>
    <div :aria-busy="state === 'loading'">
       {{ quiz }}<br />
    <br />
    </div>
    <div>
      <!--{{ quiz.questions[0].question }}
      <br />
      <br />
      {{ quiz.questions[0].choices }}
      <br />
      <br />
      {{ quiz.questions[0].choices[1] }}-->
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue'

const quiz = ref(null)
const loadingState = ref('loading')//Pour avoir le feedback sur l'état de chargement des données

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
      loadingState.value = 'idle'
    })
    .catch(e => {
      loadingState.value = 'error'
    })
})


</script>