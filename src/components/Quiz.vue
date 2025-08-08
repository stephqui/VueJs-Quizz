<template>
    <div>
        <h1>{{ quizProps.title }}</h1>
        <Progress :value="step" :max="quizProps.questions.length - 1" ></Progress>
        <Question :questionProps="question"/>
    </div>
</template>
<script setup>

import { computed, ref } from 'vue'
import Progress from './Progress.vue';
import Question from './Question.vue';

const props = defineProps({
    quizProps: Object
})

const step = ref(0)
const question = computed(() => props.quizProps.questions[step.value])
console.log(question)
</script>