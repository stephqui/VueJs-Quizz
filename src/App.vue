<template>
  <div class="container">
    Quiz
    <div class="margin-top:20px">
      {{ question.title }}
      separation
      <br/>
      <br/>
       <!--{{ question.questions[0] }}
      <br/>
      <br/>
      {{ question.questions[0].choices }}-->
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue'

const question = ref([])

onMounted(() => {
  const recupQuestion = fetch('../public/quiz.json')
    .then(r => r.json())
    .then(v => question.value = v)
  console.log(question)
})

</script>