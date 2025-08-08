<template>
    <div>
        <h1>{{ quizProps.title }}</h1>
        <Progress :value="step" :max="quizProps.questions.length - 1"></Progress>
        <Question :questionProps="question" />
        <ul>
            <li v-for="choice in computedChoices">
                <SelectAnswer :listAnswerProps="choice" />
            </li>
        </ul>
    </div>
</template>
<script setup>

import { computed, ref } from 'vue'
import Progress from './Progress.vue';
import Question from './Question.vue';
import SelectAnswer from './SelectAnswer.vue';

const props = defineProps({
    quizProps: Object
})

const step = ref(0)
const question = computed(() => props.quizProps.questions[step.value])
const computedChoices = computed(() => props.quizProps.questions[step.value].choices)
</script>