<template>
    <div class="question">
        <h3> {{ questionProps.question }}</h3>
        <ul>
            <li v-for="(choice, index) in randomChoices" :key="choice">
                <Answer :id="`answer${index}`" :props-disabled="hasAnswer" 
                :props-value="choice"
                @change="onAnswer"
                v-model="refAnswer"
                    :correctAnswer="questionProps.correct_answer" />
            </li>
        </ul>
    </div>
</template>

<script setup>
import { shuffleArray } from '@/functions/array';
import { computed, onMounted, onUnmounted, ref, watch } from 'vue';
import Answer from './Answer.vue';

const props = defineProps({
    questionProps: Object
})

const emits = defineEmits(['answer'])
const refAnswer = ref(null)
const hasAnswer = computed(() => refAnswer.value !== null)
const randomChoices = computed(() => shuffleArray(props.questionProps.choices))
let timer

const onAnswer = () => {
    clearTimeout(timer)
    timer = setTimeout(() => {
        emits('answer', refAnswer.value)
    }, 1_500)
}

onMounted(() => {
    timer = setTimeout(() => {
        refAnswer.value=''
        onAnswer()
    }, 4_000);
})
onUnmounted(() => {
    clearTimeout(timer)
})

</script>

<style>
.question {
    padding-top: 2rem;
}

.question button {
    margin-left: auto;
    display: block;
}
</style>