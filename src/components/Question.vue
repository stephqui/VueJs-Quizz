<template>
    <div class="question">
        <h3> {{ questionProps.question }}</h3>
        <ul>
            <li v-for="(choice, index) in questionProps.choices" :key="choice">
                <label :for="`answer${index}`">
                    <input :id="`answer${index}`" type="radio" name="answer" v-model="refAnswer" :value="choice">
                    {{ choice }}
                </label>
            </li>
        </ul>
        <button :disabled="!hasAnswer" @click="emits('answer', refAnswer)">Question suivante</button>
    </div>
</template>

<script setup>
import { computed, ref, watch } from 'vue';

const props = defineProps({
    questionProps: Object
})

const emits = defineEmits(['answer'])
const refAnswer = ref(null)
const hasAnswer = computed(() => refAnswer.value !== null)

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