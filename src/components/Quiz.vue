<template>
    <div>
        <h1>{{ quizProps.title }}</h1>
        <Progress :value="step" :max="quizProps.questions.length - 1"></Progress>
        <Question :questionProps="question" />

        <SelectAnswer v-for="choice in computedChoices" :listAnswerProps="choice" />

        <div>Picked: {{ picked }}</div>

        <input type="radio" value="Un" v-model="picked" />
        <label >{{question.choices[0]}}</label>

        <input type="radio" value="Deux" v-model="picked" />
        <label >{{question.choices[1]}}</label>

    </div>
</template>
<script setup>

import { computed, ref } from 'vue'
import Progress from './Progress.vue';
import Question from './Question.vue';
import SelectAnswer from './SelectAnswer.vue';

const picked = ref('')

const props = defineProps({
    quizProps: Object
})

const step = ref(0)
const question = computed(() => props.quizProps.questions[step.value])
const computedChoices = computed(() => props.quizProps.questions[step.value].choices)

//Divers
/* 
*/
</script>