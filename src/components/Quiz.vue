<template>
    <div>
        <h1>{{ quizProps.title }}</h1>
        <Progress :value="step" :max="quizProps.questions.length - 1"></Progress>
        <Question :key="question.question" :questionProps="question" v-if="state === 'question'" @answer="addAnswer" />
        <Recap v-if="state === 'recap'" :answers="answers" :quiz="quizProps"/>

    </div>
</template>
<script setup>

import { computed, ref } from 'vue'
import Progress from './Progress.vue';
import Question from './Question.vue';
import Recap from './Recap.vue';

const props = defineProps({
    quizProps: Object
})

const state = ref('question')
const answers = ref(props.quizProps.questions.map(() => null))
const step = ref(0)
const question = computed(() => props.quizProps.questions[step.value])

const addAnswer = (answer) => {
    answers.value[step.value] = answer
    if (step.value === props.quizProps.questions.length - 1) {
        state.value = 'recap'
    } else {
        step.value++
    }
}

</script>